```
simulate_copula!(U::Matrix{Real}, copula::AmhCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U に対して、Ali-Mikhail-Haq コピュラ - AmhCopula(n, θ) から size(U,1) の実現値を返します。N.o. マージナルは size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> Random.seed!(43);

julia> simulate_copula!(U, AmhCopula(2, -0.5))

julia> U
4×2 Array{Float64,2}:
 0.180975  0.820073
 0.888934  0.886169
 0.408278  0.919572
 0.828727  0.335864
```
