```
nrows(X::AbstractNode)
```

Return a new node `N` such that `N() = nrows(X())` and `N(rows=rows) = nrows(X(rows=rows))`. To obtain the number of rows of data at the source of `X`, use `nrows_at_source(X)`.
