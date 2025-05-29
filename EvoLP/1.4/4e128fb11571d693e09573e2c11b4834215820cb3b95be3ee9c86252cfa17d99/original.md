```
normal_rand_vector_pop(n, μ, Σ; rng=Random.GLOBAL_RNG)
```

Generate a population of `n` vector individuals using a normal distribution with means `μ` and covariance `Σ`.

`μ` expects a vector of length *l* (i.e. length of an individual) while `Σ` expects an *l x l* matrix of covariances.

# Examples

```julia
julia> normal_rand_vector_pop(3, [0, 0], [1 0; 0 1])
3-element Vector{Vector{Float64}}:
 [-0.15290525182234904, 0.8715880371871617]
 [-1.1283800329864322, -0.9256584563613383]
 [-0.5384758126777555, -0.8141702145510666]
```
