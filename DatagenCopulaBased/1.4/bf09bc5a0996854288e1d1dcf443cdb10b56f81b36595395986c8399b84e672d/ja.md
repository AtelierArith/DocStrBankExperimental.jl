```
simulate_copula!(U::Matrix{Real}, copula::ClaytonCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U を与えると、Clayton コピュラから t 実現を返します - ClaytonCopula(n, θ) の N.o. マージナルは size(U,2) で、size(U,2) == copula.n が必要です。実現の N.o. は size(U,1) です。

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(3,2)
3×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
 0.0  0.0

julia> simulate_copula!(U, ClaytonCopula(2, 1.))

julia> U
3×2 Array{Float64,2}:
 0.562482  0.896247
 0.968953  0.731239
 0.749178  0.38015

julia> U = zeros(2,2)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(U, ClaytonCopula(2, -.5))

julia> U
2×2 Array{Float64,2}:
 0.180975  0.818017
 0.888934  0.863358
```
