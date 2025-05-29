```
similar(df::AbstractDataFrame, rows::Integer=nrow(df))
```

Create a new `DataFrame` with the same column names and column element types as `df`. An optional second argument can be provided to request a number of rows that is different than the number of rows present in `df`.

Metadata: this function preserves table-level and column-level `:note`-style metadata.
