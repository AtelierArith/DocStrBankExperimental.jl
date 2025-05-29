```
simulate_copula!(U::Matrix{Real}, copula::MarshallOlkinCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the Marshall  Olkin copula - MarshallOlkinCopula N.o. marginals is size(U,2), requires size(U,2) == copula.n

```jldoctest
julia> u = zeros(1,2)
1×2 Array{Float64,2}:
 0.0  0.0

julia> cop = MarshallOlkinCopula([1.,2.,3.])
MarshallOlkinCopula(2, [1.0, 2.0, 3.0])

julia> Random.seed!(43);

julia> simulate_copula!(u,cop)

julia> u
1×2 Array{Float64,2}:
 0.854724  0.821831
```
