```
disallowmissing!(df::DataFrame, cols=:; error::Bool=true)
```

Convert columns `cols` of data frame `df` from element type `Union{T, Missing}` to `T` to drop support for missing values.

`cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers).

If `cols` is omitted all columns in the data frame are converted.

If `error=false` then columns containing a `missing` value will be skipped instead of throwing an error.

Metadata: this function preserves table-level and column-level `:note`-style metadata.
