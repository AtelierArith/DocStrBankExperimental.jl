```
AIC(m::DBCM)
```

DBCMモデル`m`の赤池情報量基準（AIC）を計算します。モデルのパラメータは事前に計算されている必要があります。観測数がパラメータの数に対して非常に小さくなると、警告が表示されます。その場合、修正されたAIC（AICc）を使用する必要があります。

# 例

```julia-repl
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> AIC(model);
┌ Warning: 観測数がパラメータの数に対して小さいです（n/k < 40）。修正されたAIC（AICc）を使用することを検討してください。
[...]

```

[`AICc`](@ref MaxEntropyGraphs.AICc)や[`L_DBCM_reduced`](@ref MaxEntropyGraphs.L_DBCM_reduced)も参照してください。
