```
ComponentwiseModelTransform(DM::AbstractDataModel, F::Function, idxs=trues(pdim(DM))) -> DataModel
ComponentwiseModelTransform(model::Function, idxs, F::Function) -> Function
```

モデルのパラメータを与えられたスカラー関数 `F` によって変換します。これにより `newmodel(x, θ) = oldmodel(x, F.(θ))` となります。`idxs` を提供することで、関数 `F` の適用を特定のパラメータコンポーネントに制限することができます。

ベクトル値の変換については、[`ModelEmbedding`](@ref) を参照してください。
