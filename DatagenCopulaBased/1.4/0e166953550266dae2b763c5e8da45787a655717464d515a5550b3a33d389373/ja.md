```
simulate_copula!(U::Matrix{Real}, copula::GumbelCopulaRev; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U を考慮すると、逆ガンベルコピュラ - GumbelCopulaRev(n, θ) から size(U,1) の実現値を返します。N.o. マージナルは size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(2,3)
2×3 Array{Float64,2}:
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> simulate_copula!(U, GumbelCopulaRev(3, 1.5))

julia> U
2×3 Array{Flaot64,2}:
 0.259962  0.081072  0.0493259
 0.362174  0.516486  0.876051
```
