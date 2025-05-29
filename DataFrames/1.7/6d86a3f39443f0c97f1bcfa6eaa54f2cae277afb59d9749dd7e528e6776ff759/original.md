```
deleteat!(df::DataFrame, inds)
```

Delete rows specified by `inds` from a `DataFrame` `df` in place and return it.

Internally `deleteat!` is called for all columns so `inds` must be: a vector of sorted and unique integers, a boolean vector, an integer, or `Not` wrapping any valid selector.

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

julia> deleteat!(df, 2)
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      4
   2 │     3      6
```
