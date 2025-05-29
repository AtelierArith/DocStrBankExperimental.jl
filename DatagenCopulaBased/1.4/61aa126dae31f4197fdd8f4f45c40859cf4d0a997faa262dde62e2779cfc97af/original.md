```
simulate_copula!(U::Matrix{Real}, copula::NestedClaytonCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the nested Clayton copula - NestedClaytonCopula N.o. marginals is size(U,2), these must be euqal to n.o. marginals of the copula

```jldoctest

julia> c1 = ClaytonCopula(2, 2.)
ClaytonCopula(2, 2.0)

julia> c2 = ClaytonCopula(2, 3.)
ClaytonCopula(2, 3.0)

julia> cp = NestedClaytonCopula([c1, c2], 1, 1.1)
NestedClaytonCopula(ClaytonCopula[ClaytonCopula(2, 2.0), ClaytonCopula(2, 3.0)], 1, 1.1)

julia> U = zeros(5,5)
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(U, cp)

julia> U
5×5 Array{Float64,2}:
 0.514118  0.84089    0.870106   0.906233  0.739349
 0.588245  0.85816    0.935308   0.944444  0.709009
 0.59625   0.665947   0.483649   0.603074  0.153501
 0.200051  0.304099   0.242572   0.177836  0.0851603
 0.120914  0.0683055  0.0586907  0.126257  0.519241
```
