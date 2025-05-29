```
disallowmissing(df::AbstractDataFrame, cols=:; error::Bool=true)
```

Return a copy of data frame `df` with columns `cols` converted from element type `Union{T, Missing}` to `T` to drop support for missing values.

`cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers).

If `cols` is omitted all columns in the data frame are converted.

If `error=false` then columns containing a `missing` value will be skipped instead of throwing an error.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(a=Union{Int, Missing}[1, 2])
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼────────
   1 │      1
   2 │      2

julia> disallowmissing(df)
2×1 DataFrame
 Row │ a
     │ Int64
─────┼───────
   1 │     1
   2 │     2

julia> df = DataFrame(a=[1, missing])
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼─────────
   1 │       1
   2 │ missing

julia> disallowmissing(df, error=false)
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼─────────
   1 │       1
   2 │ missing
```
