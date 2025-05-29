```
empty!(df::DataFrame)
```

Remove all rows from `df`, making each of its columns empty.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(a=1:3, b=4:6)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      4
   2 │     2      5
   3 │     3      6

julia> empty!(df)
0×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┴──────────────

julia> df.a, df.b
(Int64[], Int64[])
```
