```
simulate_copula!(U::Matrix{Real}, copula::ChainArchimedeanCopulas; rng::AbstractRNG = Random.GLOBAL_RNG)
```

事前に割り当てられた出力 U を与えると、二変量アーキメデアンコピュラの連鎖によってモデル化されたデータの size(U,1) 実現を返します。マージナルの数は size(U,2) であり、size(U,2) == copula.n が必要です。

```jldoctest
julia> c = ChainArchimedeanCopulas([4., 11.], "frank")
ChainArchimedeanCopulas(3, [4.0, 11.0], ["frank", "frank"])

julia> u = zeros(1,3)
1×3 Array{Float64,2}:
 0.0  0.0  0.0

julia> Random.seed!(43);

julia> simulate_copula!(u,c)

julia> u
1×3 Array{Float64,2}:
 0.180975  0.492923  0.679345

 julia> u = zeros(1,3)
1×3 Array{Float64,2}:
 0.0  0.0  0.0

julia> Random.seed!(43);

julia> c = ChainArchimedeanCopulas([.5, .7], ["frank", "clayton"], KendallCorrelation)
ChainArchimedeanCopulas(3, [5.736282707019972, 4.666666666666666], ["frank", "clayton"])

julia> simulate_copula!(u,c)

julia> u
1×3 Array{Float64,2}:
 0.180975  0.408582  0.646887
```
