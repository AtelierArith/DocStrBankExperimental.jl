```
simulate_copula!(U::Matrix{Real}, copula::GumbelCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U を考慮して、Gumbel copula から size(U,1) の実現値を返します - GumbelCopula(n, θ) の N.o. マージナルは size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> Random.seed!(43);

julia> U = zeros(2,3)
2×3 Array{Float64,2}:
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> simulate_copula!(U, GumbelCopula(3, 1.5))

julia> U
2×3 Array{Float64,2}:
 0.740038  0.918928  0.950674
 0.637826  0.483514  0.123949
```
