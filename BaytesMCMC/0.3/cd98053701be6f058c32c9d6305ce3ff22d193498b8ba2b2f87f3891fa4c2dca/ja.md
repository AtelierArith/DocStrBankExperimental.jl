```julia
struct MCMCDefault{K<:NamedTuple, S<:BaytesMCMC.ConfigStepsize, P<:BaytesMCMC.ConfigProposal, G, I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

MCMCコンストラクタのデフォルト引数。

# フィールド

  * `kernel::NamedTuple`: 異なるMCMCカーネルを調整するための個別のキーワード引数。
  * `stepsize::BaytesMCMC.ConfigStepsize`: 適応のためのステップサイズのデフォルト設定。
  * `proposal::BaytesMCMC.ConfigProposal`: 適応のための提案分布のデフォルト設定。
  * `GradientBackend::Any`: MCMCステップで使用される勾配バックエンド。メトロポリスサンプラーが選択された場合は使用されません。
  * `init::ModelWrappers.AbstractInitialization`: 初期モデルパラメータを取得するためのメソッド、'AbstractInitialization'を参照。
  * `generated::BaytesCore.UpdateBool`: 対応するモデルのためにgenerate(_rng, objective)がMCMC診断に保存されているかどうかのブール値。
