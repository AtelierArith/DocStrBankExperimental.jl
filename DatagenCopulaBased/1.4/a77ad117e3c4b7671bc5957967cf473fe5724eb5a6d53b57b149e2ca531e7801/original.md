```
simulate_copula!(U::Matrix{Real}, copula::AmhCopulaRev; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the reversed Ali-Mikhail-Haq copula a - AmhCopulaRev(n, θ) N.o. marginals is size(U,2), requires size(U,2) == copula.n

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(4,2)
4×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
 0.0  0.0
 0.0  0.0

julia> simulate_copula!(U, AmhCopulaRev(2, 0.5))

julia> U
4×2 Array{Float64,2}:
 0.516061   0.116089
 0.0379356  0.334231
 0.292457   0.74958
 0.0845089  0.505477
```
