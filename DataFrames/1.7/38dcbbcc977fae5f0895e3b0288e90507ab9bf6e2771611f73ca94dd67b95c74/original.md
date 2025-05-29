```
mapcols(f::Union{Function, Type}, df::AbstractDataFrame; cols=All())
```

Return a `DataFrame` where each column of `df` selected by `cols` (by default, all columns) is transformed using function `f`. Columns not selected by `cols` are copied.

`f` must return `AbstractVector` objects all with the same length or scalars (all values other than `AbstractVector` are considered to be a scalar).

The `cols` column selector can be any value accepted as column selector by the `names` function.

Note that `mapcols` guarantees not to reuse the columns from `df` in the returned `DataFrame`. If `f` returns its argument then it gets copied before being stored.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(x=1:4, y=11:14)
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14

julia> mapcols(x -> x.^2, df)
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     4    144
   3 │     9    169
   4 │    16    196

julia> mapcols(x -> x.^2, df, cols=r"y")
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     2    144
   3 │     3    169
   4 │     4    196
```
