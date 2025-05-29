```
select(df::DTable, args...; copycols::Bool=true, renamecols::Bool=true)
```

Create a new DTable that contains columns from `df` specified by `args` and return it. The result is guaranteed to have the same number of rows as df, except when no columns are selected (in which case the result has zero rows).

This operation is supposed to provide the same functionality and syntax as `DataFrames.select`, but for DTable input. Most cases should be covered and the output should be exactly the same as one obtained using DataFrames. In case of output differences or `args` causing errors please file an issue with reproduction steps and data.

Please refer to DataFrames documentation for more details on usage.
