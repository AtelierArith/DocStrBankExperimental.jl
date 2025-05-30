```julia
struct OptimDefault{T<:NamedTuple, G, I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Optimコンストラクタのデフォルト引数。

# フィールド

  * `kernel::NamedTuple`: 各Optimizerのチューニング引数
  * `GradientBackend::Any`: 最適化ステップで使用される勾配バックエンド。メトロポリスサンプラーが選択されている場合は使用されません。
  * `init::ModelWrappers.AbstractInitialization`: 初期モデルパラメータを取得するためのメソッド、'AbstractInitialization'を参照。
  * `generated::BaytesCore.UpdateBool`: 対応するモデルのためにgenerate(_rng, objective)が最適化診断に保存されているかどうかのブール値。
