```
simulate_copula!(U::Matrix{Real}, copula::FrechetCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U に対して、Frechet コピュラから size(U,1) の実現値を返します - FrechetCopula のマージナル数は size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> f = FrechetCopula(3, 0.5)
FrechetCopula(3, 0.5, 0.0)

julia> u = zeros(1,3)
1×3 Array{Real,2}:
 0.0  0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(u,f)

julia> u
1×3 Array{Real,2}:
 0.180975  0.775377  0.888934
```
