```
simulate_copula!(U::Matrix{Real}, copula::FrankCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the Frank copula- FrankCopula(n, θ) N.o. marginals is size(U,2), requires size(U,2) == copula.n

```jldoctest
julia> U = zeros(4,2)
4×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
 0.0  0.0
 0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(U, FrankCopula(2, 3.5))

julia> U
4×2 Array{Float64,2}:
 0.650276  0.910212
 0.973726  0.789701
 0.690966  0.358523
 0.747862  0.29333
```
