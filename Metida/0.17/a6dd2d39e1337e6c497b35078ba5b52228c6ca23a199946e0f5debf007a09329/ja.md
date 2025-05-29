```
LMM(model, data; contrasts=Dict{Symbol,Any}(),  random::Union{Nothing, VarEffect, Vector{VarEffect}} = nothing, repeated::Union{Nothing, VarEffect} = nothing, wts::Union{Nothing, AbstractVector, AbstractMatrix, AbstractString, Symbol} = nothing)
```

線形混合モデルオブジェクトを作成します。

`model`: 固定効果モデル（`@formula`）

`data`: 表形式のデータ

`contrasts`: 固定因子のコントラスト

`random`: ランダム効果のベクトルまたは単一のランダム効果

`repeated`: 繰り返し効果またはベクトル

`wts`: 回帰重み（残差）。

重みは `Symbol` または `String` として設定できます。この場合、重みは表形式のデータから取得されます。重みがベクトルの場合、このベクトルは共分散行列のR側部分に適用されます（[Weights details](@ref weights_header)を参照）。重みが行列の場合、共分散行列のR側部分は重み行列の対応する部分で乗算されます。

また、[`@lmmformula`](@ref)も参照してください。
