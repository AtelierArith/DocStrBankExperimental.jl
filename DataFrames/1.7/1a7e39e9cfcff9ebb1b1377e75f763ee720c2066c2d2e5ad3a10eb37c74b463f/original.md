```
repeat!(df::DataFrame, count::Integer)
```

Update a data frame `df` in-place by repeating its rows the number of times specified by `count`. Columns of `df` are freshly allocated.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Example

```jldoctest
julia> df = DataFrame(a=1:2, b=3:4)
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4

julia> repeat(df, 2)
4×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4
   3 │     1      3
   4 │     2      4
```
