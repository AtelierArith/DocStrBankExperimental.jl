```
simulate_copula!(U::Matrix{Real}, copula::AmhCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the Ali-Mikhail-Haq copula- AmhCopula(n, θ) N.o. marginals is size(U,2), requires size(U,2) == copula.n

```jldoctest
julia> Random.seed!(43);

julia> simulate_copula!(U, AmhCopula(2, -0.5))

julia> U
4×2 Array{Float64,2}:
 0.180975  0.820073
 0.888934  0.886169
 0.408278  0.919572
 0.828727  0.335864
```
