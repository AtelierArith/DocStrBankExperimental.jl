```
ModelEmbedding(DM::AbstractDataModel, F::Function, start::AbstractVector; Domain::HyperCube=FullDomain(length(start),Inf)) -> DataModel
```

モデル関数を `newmodel(x, θ) = oldmodel(x, F(θ))` を介して変換し、関連する `DataModel` を返します。初期パラメータ構成 `start` および `Domain` をオプションで `DataModel` コンストラクタに渡すことができます。

成分ごとの変換については [`ComponentwiseModelTransform`](@ref) を参照してください。
