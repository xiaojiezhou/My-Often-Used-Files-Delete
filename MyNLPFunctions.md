<a id="table-of-contents"></a>
## My NLP R Functions - Table of Contents
* [replace.words: replace words listed in col 1 by words in col 2](#replace-words)
* [TempJunks](#TmpJunks)
    - [spacehold] (#spaceholder)

    
<div id='replace-words'/>   
### -- Replacing words in ListA by words in ListB --

    # -- Read in lookup table
    require(XLConnect)
    wb = loadWorkbook("C:\\Users\\zhou.x\\Desktop\\Other\\DataScience\\TextAnalytics\\ReplacementWords.xlsx", create = TRUE)
    Dict = readWorksheet(wb, sheet = "sheet1", startCol = 1, endCol = 2, header=TRUE)
    head(Dict)
    # Dict = apply(Dict, c(1,2), trimws)

    # -- messy list
    mytext <- c("I couldnt move",
               "he wont go",
               "i dont feel well",
               "I wasnt aware of this")
    
    # -- replace.words function
    replace.words <- function( txt, dict){
        dict = apply(dict, c(1,2), trimws)
        
        for(x in 1:nrow(dict))
            txt <- gsub(dict[x,"Org"],dict[x,"Rplc"], txt)
        return(txt)
    }
    #replace.words(mytext, Dict)










<div id='TmpJunks'/>   
program='C:\\Program Files (x86)\\Aspell\\bin\\aspell.exe'
junk<-aspell(as.factor("interface"),program=program)


install.packages("Aspell", repos = "http://www.omegahat.org/R", version='3.0')




##### check with Hongxiang about SVD 

td = tempfile()
dir.create(td)
write( c("dog", "cat", "mouse"), file=paste(td, "D1", sep="/"))
write( c("hamster", "mouse", "sushi"), file=paste(td, "D2", sep="/"))
write( c("dog", "monster", "monster"), file=paste(td, "D3", sep="/"))
write( c("dog", "mouse", "dog"), file=paste(td, "D4", sep="/"))



library(tm)
myCorpus <- c("Quick response", 
              "respond quick and was very helpful",
              "A quick reply",
              "The situation was resolved quick and efficient.",
              "fast response",
              "I am happy with how quick it was handled.",
              "Understand my query.",
              "Understand exactly what I needed !!",
              "Understand my complaint right from the start and did not attempt to argue",
              "Very positive and understand",
              "Very understand",
              "Very understand and accommodate.",
              "response quick")
corpus <- Corpus(VectorSource(myCorpus))
myMatrix = TermDocumentMatrix(corpus)

myMatrix = as.matrix(myMatrix)


### R spell check ###

# check_spelling <- function(text) {
# Create a file with on each line one of the words we want to check
text <- gsub("[,.]", "", text)
text <- strsplit(text, " ", fixed=TRUE)[[1]]
filename <- tempfile()
writeLines(text, con = filename);
# Check spelling of file using aspell
result <- aspell(filename, "Rd")
# Extract list of suggestions from result
suggestions <- result$Suggestions
names(suggestions) <- result$Original
unlink(filename)
suggestions
}

text <- "I am text mining a large database to create indicator variables which indicate the occurence of certain phrases in a comments field of an observation. The comments were entered by technicians, so the terms used are always consistent. "
check_spelling(text)


$occurence
[1] "occurrence"   "occurrences"  "occurrence's"



install.packages("KernSmooth")
library(KernSmooth)


library(koRpus)
tagged.text <- treetag("C:\\Treetagger\\INSTALL.txt", treetagger="manual",
                       lang="en", TT.options=c(path="C:\\treetagger", preset="en"))


tagged.results <- treetag(c("run", "ran", "running"), treetagger="manual", format="obj",
                          TT.tknz=FALSE , lang="en",
                          TT.options=list(path="C:/TreeTagger", preset="en"))
tagged.results@TT.res


agged.results <- treetag(c("run", "ran", "running"),  format="obj",
                         TT.tknz=FALSE , lang="en",
                         treetagger="C:/treetagger/cmd/tree-tagger-english")

agged.results <- treetag(c("run", "ran", "running"), treetagger="manual", 
                            lang="en",
                            TT.options=list(path="C:/Users/zhou.x/Desktop/Other/Data Science/TextAnalytics/TreeTagger/bin/", 
                            preset="en"))


library(wordnet)
setDict(pathData = "C:/Program Files (x86)/WordNet/2.1/dict/")

filter <- getTermFilter("ExactMatchFilter", "hot", TRUE)
terms <- getIndexTerms("ADJECTIVE", 1, filter)
synsets <- getSynsets(terms[[1]])
related <- getRelatedSynsets(synsets[[1]], "!")
sapply(synsets, getWord)

sapply(related, getWord)

synonyms("what", "NOUN")
synonyms("corrupt", "VERB")
synonyms("CAR", "NOUN")

