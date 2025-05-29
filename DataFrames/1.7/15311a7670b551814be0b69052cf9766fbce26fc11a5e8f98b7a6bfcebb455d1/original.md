```
copy(df::DataFrame; copycols::Bool=true)
```

Copy data frame `df`. If `copycols=true` (the default), return a new  `DataFrame` holding copies of column vectors in `df`. If `copycols=false`, return a new `DataFrame` sharing column vectors with `df`.

Metadata: this function preserves all table-level and column-level metadata.
