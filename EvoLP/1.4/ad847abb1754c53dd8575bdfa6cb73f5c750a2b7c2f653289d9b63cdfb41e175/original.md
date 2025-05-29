```
unif_rand_vector_pop(n, lb, ub; rng=Random.GLOBAL_RNG)
```

Generate a population of `n` vector individuals using a uniformly random distribution between lower bounds `lb` and upper bounds `ub`.

Both `lb` and `ub` must be arrays of the same dimensions.

# Examples

```julia
julia> unif_rand_vector_pop(3, [-1, -1], [1, 1])
3-element Vector{Vector{Float64}}:
 [-0.16338687344459046, 0.31576097298524064]
 [-0.941510876597899, 0.8219576462978224]
 [-0.377090051761797, -0.28434454028992096]
```
