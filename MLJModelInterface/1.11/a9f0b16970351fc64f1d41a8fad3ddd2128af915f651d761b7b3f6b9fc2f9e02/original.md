```
select(X, r, c)
```

Select element(s) of a table or matrix at row(s) `r` and column(s) `c`. An object of the sink type of `X` (or a matrix) is returned unless `c` is a single integer or symbol. In that case a vector is returned, unless `r` is a single integer, in which case a single element is returned.

See also: [`selectrows`](@ref), [`selectcols`](@ref).
