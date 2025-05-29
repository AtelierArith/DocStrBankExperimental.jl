```
calc_tfidf(X, idf)
```

Calculate the term frequency - inverse document infrequency matrix. Optimised for sparse matrices.  Mathematically equivalent to `X .* idf` followed by `normalize!`
