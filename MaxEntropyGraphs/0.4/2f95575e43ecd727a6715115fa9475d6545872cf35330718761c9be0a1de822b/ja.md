```
AICc(m::BiCM)
```

BiCMモデル`m`の修正赤池情報量基準（AICc）を計算します。モデルのパラメータは事前に計算されている必要があります。

# 例

```jldoctest
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> AICc(model)
432.12227535579956

```

他にも[`AIC`](@ref MaxEntropyGraphs.AIC)、[`L_BiCM_reduced`](@ref MaxEntropyGraphs.L_BiCM_reduced)を参照してください。
