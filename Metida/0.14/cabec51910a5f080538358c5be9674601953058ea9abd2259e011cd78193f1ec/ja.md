```
LMM(model, data; contrasts=Dict{Symbol,Any}(),  random::Union{Nothing, VarEffect, Vector{VarEffect}} = nothing, repeated::Union{Nothing, VarEffect} = nothing)
```

線形混合モデルオブジェクトを作成します。

`model`: 固定効果モデル（`@formula`）

`data`: 表形式のデータ

`contrasts`: 固定因子のコントラスト

`random`: ランダム効果のベクトルまたは単一のランダム効果

`repeated`: 繰り返し効果（1つのみ）

参照: [`@lmmformula`](@ref)
