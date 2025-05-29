```
mapcols!(f::Union{Function, Type}, df::DataFrame; cols=All())
```

Update a `DataFrame` in-place where each column of `df` selected by `cols` (by default, all columns) is transformed using function `f`. Columns not selected by `cols` are left unchanged.

`f` must return `AbstractVector` objects all with the same length or scalars (all values other than `AbstractVector` are considered to be a scalar).

Note that `mapcols!` reuses the columns from `df` if they are returned by `f`.

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

julia> mapcols!(x -> x.^2, df);

julia> df
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     4    144
   3 │     9    169
   4 │    16    196

julia> mapcols!(x -> 2 * x, df, cols=r"x");

julia> df
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     2    121
   2 │     8    144
   3 │    18    169
   4 │    32    196
```
