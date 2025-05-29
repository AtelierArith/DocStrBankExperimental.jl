```
simulate_copula!(U::Matrix{Real}, copula::ClaytonCopulaRev; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U を考慮して、逆クレイトンコピュラ - ClaytonCopulaRev(n, θ) から size(U,1) の実現値を返します。マージナルの数は size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(2,2)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0

julia> simulate_copula!(U, ClaytonCopulaRev(2, -0.5))

julia> U
2×2 Array{Float64,2}:
 0.819025  0.181983
 0.111066  0.136642

 julia> Random.seed!(43);

julia> U = zeros(2,2)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0

julia> simulate_copula!(U, ClaytonCopulaRev(2, 2.))

julia> U
2×2 Array{Float64,2}:
 0.347188   0.087281
 0.0257036  0.212676
```
