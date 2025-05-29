```
subcolumns(data, names, rows=Colon(); nomissing=true)
```

Construct a [`VecColumnTable`](@ref) from `data` using columns specified with `names` over selected `rows`.

By default, columns are converted to drop support for missing values. When possible, resulting columns share memory with original columns.
