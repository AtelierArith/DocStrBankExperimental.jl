```
TermMatrix(corpus, vocab; pattern=r"\w\w+\b")
TermMatrix(matrix, features)
```

Calculate the term matrix of nwords × ndocuments for a corpus. Each column corresponds to a document and each row to the number of occurances of a given term in each document.

`tm.matrix` => a sparse matrix representation of the term matrix.

`tm.features` => a dictionary which maps terms to row numbers.
