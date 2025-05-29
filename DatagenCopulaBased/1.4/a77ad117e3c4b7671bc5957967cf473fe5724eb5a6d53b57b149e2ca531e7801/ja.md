```
simulate_copula!(U::Matrix{Real}, copula::AmhCopulaRev; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U を与えると、逆アリ-ミハイル-ハクコピュラ a - AmhCopulaRev(n, θ) から size(U,1) の実現値を返します。マージナルの数は size(U,2) であり、size(U,2) == copula.n が必要です。

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
