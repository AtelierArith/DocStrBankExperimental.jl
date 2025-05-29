```
selectrows(X, r)
```

Select single or multiple rows from a table, abstract vector or matrix `X`. If `X` is tabular, the object returned is a table of the preferred sink type of `typeof(X)`, even if only a single row is selected.

If the object is neither a table, abstract vector or matrix, `X` is returned and `r` is ignored.
