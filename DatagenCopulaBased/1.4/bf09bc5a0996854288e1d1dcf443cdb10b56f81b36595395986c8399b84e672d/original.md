```
simulate_copula!(U::Matrix{Real}, copula::ClaytonCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns t realizations from the Clayton copula - ClaytonCopula(n, θ) N.o. marginals is size(U,2), requires size(U,2) == copula.n. N.o. realisations is size(U,1).

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(3,2)
3×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
 0.0  0.0

julia> simulate_copula!(U, ClaytonCopula(2, 1.))

julia> U
3×2 Array{Float64,2}:
 0.562482  0.896247
 0.968953  0.731239
 0.749178  0.38015

julia> U = zeros(2,2)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(U, ClaytonCopula(2, -.5))

julia> U
2×2 Array{Float64,2}:
 0.180975  0.818017
 0.888934  0.863358
```
