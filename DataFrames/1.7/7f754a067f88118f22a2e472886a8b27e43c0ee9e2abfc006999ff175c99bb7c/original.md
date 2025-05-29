```
repeat!(df::DataFrame; inner::Integer=1, outer::Integer=1)
```

Update a data frame `df` in-place by repeating its rows. `inner` specifies how many times each row is repeated, and `outer` specifies how many times the full set of rows is repeated. Columns of `df` are freshly allocated.

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

julia> repeat!(df, inner=2, outer=3);

julia> df
12×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     1      3
   3 │     2      4
   4 │     2      4
   5 │     1      3
   6 │     1      3
   7 │     2      4
   8 │     2      4
   9 │     1      3
  10 │     1      3
  11 │     2      4
  12 │     2      4
```
