```
AIC(m::BiCM)
```

BiCMモデル`m`の赤池情報量基準（AIC）を計算します。モデルのパラメータは事前に計算されている必要があります。観測データの数がパラメータの数に対してあまりにも小さくなると、警告が表示されます。その場合、修正されたAIC（AICc）を使用する必要があります。

# 例

```julia
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> AIC(model);
[...]

```

他にも[`AICc`](@ref MaxEntropyGraphs.AICc)、[`L_BiCM_reduced`](@ref MaxEntropyGraphs.L_BiCM_reduced)を参照してください。
