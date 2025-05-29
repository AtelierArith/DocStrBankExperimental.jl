```
simulate_copula!(U::Matrix{Real}, copula::NestedGumbelCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U に対して、ネストされたガンベルコピュラから size(U,1) の実現値を返します - NestedGumbelCopula のマージナルの数は size(U,2) であり、これらはコピュラのマージナルの数と等しくなければなりません。

```jldoctest
julia> c1 = GumbelCopula(2, 2.)
GumbelCopula(2, 2.0)

julia> c2 = GumbelCopula(2, 3.)
GumbelCopula(2, 3.0)

julia> cp = NestedGumbelCopula([c1, c2], 1, 1.1)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 2.0), GumbelCopula(2, 3.0)], 1, 1.1)

julia> u = zeros(4,5)
4×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(u, cp)

julia> u
4×5 Array{Float64,2}:
 0.387085   0.693399   0.94718   0.953776  0.583379
 0.0646972  0.0865914  0.990691  0.991127  0.718803
 0.966896   0.709233   0.788019  0.855622  0.755476
 0.272487   0.106996   0.756052  0.834068  0.661432
```
