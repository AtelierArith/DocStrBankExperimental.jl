```
p = outer_product([rng::AbstractRNG,] dists::Vector{<:Distribution}, N=100_000)
```

Creates a multivariate systematic sample where each dimension is sampled according to the corresponding univariate distribution in `dists`. Returns `p::Vector{Particles}` where each Particles has a length approximately equal to `N`. The particles form the outer product between `d` systematically sampled vectors with length given by the d:th root of N, where `d` is the length of `dists`, All particles will be independent and have marginal distributions given by `dists`.

See also `MonteCarloMeasurements.⊗`
