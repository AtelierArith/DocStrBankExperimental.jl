```
AICc(m::UBCM)
```

UBCMモデル`m`の修正アカイケ情報量基準（AICc）を計算します。モデルのパラメータは事前に計算されている必要があります。

# 例

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> AICc(model)
409.891217554954

```

参照してください [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_UBCM_reduced`](@ref MaxEntropyGraphs.L_UBCM_reduced).
