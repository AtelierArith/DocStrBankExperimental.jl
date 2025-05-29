```
reverse(df::AbstractDataFrame, start=1, stop=nrow(df))
```

Return a data frame containing the rows in `df` in reversed order. If `start` and `stop` are provided, only rows in the `start:stop` range are affected.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(a=1:5, b=6:10, c=11:15)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      6     11
   2 │     2      7     12
   3 │     3      8     13
   4 │     4      9     14
   5 │     5     10     15

julia> reverse(df)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     5     10     15
   2 │     4      9     14
   3 │     3      8     13
   4 │     2      7     12
   5 │     1      6     11

julia> reverse(df, 2, 3)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      6     11
   2 │     3      8     13
   3 │     2      7     12
   4 │     4      9     14
   5 │     5     10     15
```
