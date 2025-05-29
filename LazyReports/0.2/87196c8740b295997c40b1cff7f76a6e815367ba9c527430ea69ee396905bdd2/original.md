```
lazytable(tbl; headers = missing)
```

Wrap/convert a Tables.jl-compatible `tbl` an return a `LazyTable`, for use with [`lazyreport`](@ref).

If `headers` is `missing`, default headers are generated from the column names of `tbl`. If `headers` is an `AbstractDict`, the default column names are overridden according to the keys and values in it. If `headers` is an `AbstractVector`, it explicitly defines all headers of the table and must have the same length as the number of columns in `tbl`.
