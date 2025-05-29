```
simulate_copula!(U::Matrix{Real}, copula::HierarchicalGumbelCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

Given the preallocated output U, Returns size(U,1) realizations from the hierachically nested Gumbel copula - HierarchicalGumbelCopula N.o. marginals is size(U,2), these must be euqal to n.o. marginals of the copula i.e. copula.n

```jldoctest

julia> c = HierarchicalGumbelCopula([5., 4., 3.])
HierarchicalGumbelCopula(4, [5.0, 4.0, 3.0])

julia> Random.seed!(43);

julia> u = zeros(3,4)
3×4 Array{Float64,2}:
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> simulate_copula!(u, c)

julia> u
3×4 Array{Float64,2}:
 0.100353  0.207903  0.0988337  0.0431565
 0.347417  0.217052  0.223734   0.042903
 0.73617   0.347349  0.168348   0.410963
```
