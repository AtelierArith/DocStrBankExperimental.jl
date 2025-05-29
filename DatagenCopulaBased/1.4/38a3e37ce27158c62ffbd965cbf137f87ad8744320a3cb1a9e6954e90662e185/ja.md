```
simulate_copula!(U::Matrix{Real}, copula::MarshallOlkinCopula; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U に対して、Marshall Olkin コピュラから size(U,1) の実現値を返します - MarshallOlkinCopula のマージナル数は size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> u = zeros(1,2)
1×2 Array{Float64,2}:
 0.0  0.0

julia> cop = MarshallOlkinCopula([1.,2.,3.])
MarshallOlkinCopula(2, [1.0, 2.0, 3.0])

julia> Random.seed!(43);

julia> simulate_copula!(u,cop)

julia> u
1×2 Array{Float64,2}:
 0.854724  0.821831
```
