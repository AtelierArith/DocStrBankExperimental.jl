```
site_specific_frequencies(X::AbstractAlignment[, weights=X.weights]; as_vec=false)
```

Return the site specific frequencies of `X`. If `as_vec`, the result is a vector of length `Lxq`. Otherwise, it is a matrix of `q` rows and `L` columns (default).
