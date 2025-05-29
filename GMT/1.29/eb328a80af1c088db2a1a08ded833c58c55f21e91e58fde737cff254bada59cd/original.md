```
Dv = groupby(D::GMTdataset, col)::Vector{GMTdataset}
```

Split a GMTdataset by the unique values of the column selected by `col`.

`col` can be a column name, either as a String or a Symbol, or a column number. In any case, it must point to a column with integers (normaly a flint (Floating Point Integer)), or a string column. *i.e.,* the last column in a GMTdataset.
