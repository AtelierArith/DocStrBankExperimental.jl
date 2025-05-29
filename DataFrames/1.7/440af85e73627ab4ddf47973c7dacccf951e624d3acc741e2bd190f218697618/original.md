```
reverse!(df::AbstractDataFrame, start=1, stop=nrow(df))
```

Mutate data frame in-place to reverse its row order. If `start` and `stop` are provided, only rows in the `start:stop` range are affected.

`reverse!` will produce a correct result even if some columns of passed data frame are identical (checked with `===`). Otherwise, if two columns share some part of memory but are not identical (e.g. are different views of the same parent vector) then `reverse!` result might be incorrect.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

Metadata having other styles is dropped (from parent data frame when `df` is a `SubDataFrame`).

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

julia> reverse!(df)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     5     10     15
   2 │     4      9     14
   3 │     3      8     13
   4 │     2      7     12
   5 │     1      6     11

julia> reverse!(df, 2, 3)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     5     10     15
   2 │     3      8     13
   3 │     4      9     14
   4 │     2      7     12
   5 │     1      6     11
```
