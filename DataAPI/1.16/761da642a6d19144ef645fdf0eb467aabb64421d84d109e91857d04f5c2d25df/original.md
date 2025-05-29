```
colmetadatakeys(x, [col])
```

If `col` is passed return an iterator of metadata keys for which `metadata(x, col, key)` returns a metadata value. Throw an error if `x` does not support reading column metadata or if `col` is not a column of `x`.

`col` must have a type that is supported by table `x` for column indexing. Following the Tables.jl contract `Symbol` and `Int` are always allowed.

If `col` is not passed return an iterator of `col => colmetadatakeys(x, col)` pairs for all columns that have metadata, where `col` are `Symbol`. If `x` does not support column metadata return `()`.
