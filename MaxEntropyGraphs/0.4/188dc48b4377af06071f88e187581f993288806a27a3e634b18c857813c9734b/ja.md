```
AICc(m::DBCM)
```

DBCMモデル`m`の修正赤池情報量基準（AICc）を計算します。モデルのパラメータは事前に計算されている必要があります。

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> AICc(model)
314.5217467272881

```

関連情報としては [`AIC`](@ref MaxEntropyGraphs.AIC)、[`L_DBCM_reduced`](@ref MaxEntropyGraphs.L_DBCM_reduced) があります。
