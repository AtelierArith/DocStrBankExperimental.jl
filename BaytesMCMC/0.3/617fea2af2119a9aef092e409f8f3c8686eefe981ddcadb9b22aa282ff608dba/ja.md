```julia
struct MCMCTune{A<:BaytesCore.UpdateBool, B<:BaytesCore.UpdateBool, F<:AbstractFloat, T<:ModelWrappers.Tagged, E<:Tuple, P<:BaytesMCMC.Proposal} <: BaytesCore.AbstractTune
```

MCMC調整コンテナ。

# フィールド

  * `tagged::ModelWrappers.Tagged`: タグ付きパラメータ。
  * `phase::BaytesMCMC.PhaseTune`: MCMCサイクルの現在のフェーズ
  * `stepsize::BaytesMCMC.StepSizeTune`: ステップサイズコンテナ
  * `proposal::BaytesMCMC.Proposal`: 事後共分散推定のための情報
  * `generated::BaytesCore.UpdateBool`: サンプリング中に生成された量を生成するかどうかのブール値
  * `iter::BaytesCore.Iterator`: 現在のイテレーション番号
