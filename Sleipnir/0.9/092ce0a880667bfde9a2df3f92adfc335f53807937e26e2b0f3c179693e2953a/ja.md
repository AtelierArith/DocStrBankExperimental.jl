可変構造体で、氷流、質量収支、機械学習の3つのコンポーネントを表します。

```
Model{IFM <: AbstractEmptyModel, MBM <: AbstractEmptyModel, MLM <: AbstractEmptyModel}
```

# キーワード引数

  * `iceflow::Union{IFM, Vector{IFM}}`: 単一の`IFM`インスタンスまたは`IFM`インスタンスのベクトルである氷流コンポーネントを表します。
  * `mass_balance::Union{MBM, Vector{MBM}}`: 単一の`MBM`インスタンスまたは`MBM`インスタンスのベクトルである質量収支コンポーネントを表します。
  * `machine_learning::MLM`: `MLM`のインスタンスである機械学習コンポーネントを表します。

# 型パラメータ

  * `IFM`: 氷流モデルの型を表す`AbstractEmptyModel`のサブタイプです。
  * `MBM`: 質量収支モデルの型を表す`AbstractEmptyModel`のサブタイプです。
  * `MLM`: 機械学習モデルの型を表す`AbstractEmptyModel`のサブタイプです。
