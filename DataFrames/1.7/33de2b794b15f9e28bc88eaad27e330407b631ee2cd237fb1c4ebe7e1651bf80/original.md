```
allowmissing(df::AbstractDataFrame, cols=:)
```

Return a copy of data frame `df` with columns `cols` converted to element type `Union{T, Missing}` from `T` to allow support for missing values.

`cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers).

If `cols` is omitted all columns in the data frame are converted.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(a=[1, 2])
2×1 DataFrame
 Row │ a
     │ Int64
─────┼───────
   1 │     1
   2 │     2

julia> allowmissing(df)
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼────────
   1 │      1
   2 │      2
```
