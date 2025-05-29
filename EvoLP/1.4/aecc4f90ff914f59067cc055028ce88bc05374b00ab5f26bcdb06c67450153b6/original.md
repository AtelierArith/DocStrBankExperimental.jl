```
binary_vector_pop(n, l; rng=Random.GLOBAL_RNG)
```

Generate a population of `n` vector binary individuals, each of length `l`.

# Examples

```julia
julia> using EvoLP

julia> binary_vector_pop(2, 5)
2-element Vector{BitVector}:
 [1, 0, 1, 1, 0]
 [0, 1, 0, 0, 0]
```
