```
permutation_vector_pop(n, d, pool; replacement=false, rng=Random.GLOBAL_RNG)
```

Generate a population of `n` permutation vector individuals, of size `d` and with values sampled from `pool`. Usually `d` would be equal to `length(pool)`.

Sampling is **without replacement** by default (generating permutations if `pool` is a set). When `replacement=true` then it generates combinations of (possibly) repeated values.

# Examples

```julia
julia> permutation_vector_pop(1, 8, 1:8)
1-element Vector{Vector{Int64}}:
 [7, 3, 8, 1, 5, 6, 4, 2]

julia> permutation_vector_pop(2, 5, ["a", "b", "c", "d", "e"]; replacement=false)
2-element Vector{Vector{String}}:
 ["e", "b", "c", "d", "a"]
 ["b", "d", "a", "e", "c"]
```
