```
simulate_copula!(U::Matrix{Real}, copula::NestedFrankCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U に対して、ネストされたフランクコピュラから size(U,1) の実現値を返します - ネストされたフランクコピュラのマージナルの数は size(U,2) であり、これらはコピュラのマージナルの数と等しくなければなりません。

```jldoctest

julia> c1 = FrankCopula(2, 4.)
FrankCopula(2, 4.0)

julia> c2 = FrankCopula(2, 5.)
FrankCopula(2, 5.0)

julia> c = NestedFrankCopula([c1, c2],1, 2.0)
NestedFrankCopula(FrankCopula[FrankCopula(2, 4.0), FrankCopula(2, 5.0)], 1, 2.0)

julia> U = zeros(1,5)
1×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(U, c)

julia> U
1×5 Array{Float64,2}:
 0.642765  0.901183  0.969422  0.9792  0.74155

```
