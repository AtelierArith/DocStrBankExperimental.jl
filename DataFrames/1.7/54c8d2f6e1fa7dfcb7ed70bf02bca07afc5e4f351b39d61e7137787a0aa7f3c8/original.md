```
allowmissing!(df::DataFrame, cols=:)
```

Convert columns `cols` of data frame `df` from element type `T` to `Union{T, Missing}` to support missing values.

`cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers).

If `cols` is omitted all columns in the data frame are converted.

Metadata: this function preserves table-level and column-level `:note`-style metadata.
