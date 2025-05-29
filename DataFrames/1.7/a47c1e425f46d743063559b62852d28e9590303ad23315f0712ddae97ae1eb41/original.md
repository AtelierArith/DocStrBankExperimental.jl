```
shuffle!([rng=GLOBAL_RNG,] df::AbstractDataFrame)
```

Randomly permute rows of `df` in-place. The optional `rng` argument specifies a random number generator.

`shuffle!` will produce a correct result even if some columns of passed data frame are identical (checked with `===`). Otherwise, if two columns share some part of memory but are not identical (e.g. are different views of the same parent vector) then `shuffle!` result might be incorrect.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

Metadata having other styles is dropped (from parent data frame when `df` is a `SubDataFrame`).

# Examples

```jldoctest
julia> using Random

julia> rng = MersenneTwister(1234);

julia> shuffle!(rng, DataFrame(a=1:5, b=1:5))
5×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     2      2
   2 │     1      1
   3 │     4      4
   4 │     3      3
   5 │     5      5
```
