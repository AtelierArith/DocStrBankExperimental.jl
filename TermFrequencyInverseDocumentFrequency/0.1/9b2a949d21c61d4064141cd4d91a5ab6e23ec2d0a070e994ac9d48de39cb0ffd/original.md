```
select_vocabulary(corpus; 
    min_document_frequency=1, transform=identity, pattern=r"\w\w+\b", stopwords=Set{String}())
```

Select words from the corpus based on the rules defined by the key word arguments. Stop words are excluded from the vocabulary list. Use `stopwords=default_stop_words()` to get a list of words from Sci-kit Learn. 
