```
simulate_copula!(U::Matrix{Real}, copula::NestedAmhCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the nested AMH copula - NestedAmhCopula N.o. marginals is size(U,2), these must be euqal to n.o. marginals of the copula

```jldoctest

julia> c1 = AmhCopula(2, .7)
AmhCopula(2, 0.7)

julia> c2 = AmhCopula(2, .8)
AmhCopula(2, 0.8)

julia> cp = NestedAmhCopula([c1, c2], 1, 0.2)
NestedAmhCopula(AmhCopula[AmhCopula(2, 0.7), AmhCopula(2, 0.8)], 1, 0.2)

julia> Random.seed!(43);

julia> U = zeros(4,5)
4×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> simulate_copula!(U, cp)

julia> U
4×5 Array{Float64,2}:
 0.557393  0.902767  0.909853  0.938522  0.586068
 0.184204  0.866664  0.699134  0.226744  0.102932
 0.268634  0.383355  0.179023  0.533749  0.995958
 0.578143  0.840169  0.743728  0.963226  0.576695
```
