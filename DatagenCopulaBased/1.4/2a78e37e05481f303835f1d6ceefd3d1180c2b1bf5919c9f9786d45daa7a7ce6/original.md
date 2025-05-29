```
simulate_copula!(U::Matrix{Real}, copula::GumbelCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the Gumbel copula -  GumbelCopula(n, θ) N.o. marginals is size(U,2), requires size(U,2) == copula.n

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(2,3)
2×3 Array{Float64,2}:
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> simulate_copula!(U, GumbelCopula(3, 1.5))

julia> U
2×3 Array{Float64,2}:
 0.740038  0.918928  0.950674
 0.637826  0.483514  0.123949
```
