```
last(df::AbstractDataFrame, n::Integer; view::Bool=false)
```

Get a data frame with the `n` last rows of `df`. Get all rows if `n` is greater than the number of rows in `df`. Error if `n` is negative.

If `view=false` a freshly allocated `DataFrame` is returned. If `view=true` then a `SubDataFrame` view into `df` is returned.

Metadata: this function preserves table-level and column-level `:note`-style metadata.
