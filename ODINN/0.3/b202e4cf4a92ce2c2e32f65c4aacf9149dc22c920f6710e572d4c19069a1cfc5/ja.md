```
Model(; iceflow::Union{IFM, Vector{IFM}, Nothing}, mass_balance::Union{MBM, Vector{MBM}, Nothing}, machine_learning::Union{MLM, Nothing}) where {IFM <: IceflowModel, MBM <: MBmodel, MLM <: MLmodel}
```

提供されたiceflow、質量バランス、および機械学習コンポーネントを使用して新しいモデルインスタンスを作成します。

# 引数

  * `iceflow::Union{IFM, Vector{IFM}, Nothing}`: 使用するiceflowモデル。単一のモデル、モデルのベクトル、または`nothing`であることができます。
  * `mass_balance::Union{MBM, Vector{MBM}, Nothing}`: 使用する質量バランスモデル。単一のモデル、モデルのベクトル、または`nothing`であることができます。
  * `machine_learning::Union{MLM, Nothing}`: 使用する機械学習モデル。単一のモデルまたは`nothing`であることができます。

# 戻り値

  * `model`: 提供されたコンポーネントで初期化された新しい`Sleipnir.Model`のインスタンス。
