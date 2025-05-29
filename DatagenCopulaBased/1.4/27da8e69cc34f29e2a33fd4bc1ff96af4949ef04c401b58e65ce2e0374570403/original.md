```
simulate_copula!(U::Matrix{Real}, copula::FrechetCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the Frechet copula - FrechetCopula N.o. marginals is size(U,2), requires size(U,2) == copula.n

```jldoctest
julia> f = FrechetCopula(3, 0.5)
FrechetCopula(3, 0.5, 0.0)

julia> u = zeros(1,3)
1×3 Array{Real,2}:
 0.0  0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(u,f)

julia> u
1×3 Array{Real,2}:
 0.180975  0.775377  0.888934
```
