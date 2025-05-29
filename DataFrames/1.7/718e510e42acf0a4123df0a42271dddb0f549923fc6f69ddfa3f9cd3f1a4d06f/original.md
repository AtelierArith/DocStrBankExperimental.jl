```
shuffle([rng=GLOBAL_RNG,] df::AbstractDataFrame)
```

Return a copy of `df` with randomly permuted rows. The optional `rng` argument specifies a random number generator.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> using Random

julia> rng = MersenneTwister(1234);

julia> shuffle(rng, DataFrame(a=1:5, b=1:5))
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
