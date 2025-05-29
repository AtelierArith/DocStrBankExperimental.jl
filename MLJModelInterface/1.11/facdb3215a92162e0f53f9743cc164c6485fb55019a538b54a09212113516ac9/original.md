```
selectcols(X, c)
```

Select single or multiple columns from a matrix or table `X`. If `c` is an abstract vector of integers or symbols, then the object returned is a table of the preferred sink type of `typeof(X)`. If `c` is a *single* integer or column, then an `AbstractVector` is returned.
