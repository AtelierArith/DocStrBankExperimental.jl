```
SmoothLPResult{TF<:AbstractFloat, TS<:ModelSelectionResult} <: AbstractEstimatorResult
```

スムーズなローカルプロジェクションの推定からの追加結果。 [`SmoothLP`](@ref) および [`LocalProjectionResult`](@ref) も参照してください。

# フィールド

  * `θ::Vector{TF}`: Bスプラインの係数推定値。
  * `Σ::Vector{TF}`: Bスプラインの分散共分散推定値。
  * `bm::Matrix{TF}`: Bスプラインの基底行列。
  * `λ::TF`: モデル選択からの最適スムージングパラメータ。
  * `loocv::TF`: 一つ外し交差検証誤差。
  * `rss::TF`: 残差平方和。
  * `gcv::TF`: 一般化交差検証誤差。
  * `aic::TF`: 赤池情報量基準値。
  * `dof_fit::TF`: フィットの自由度。
  * `dof_res::TF`: 残差の自由度。
  * `search::TS`: モデル選択からの追加結果。
  * `m::Ridge{TF}`: リッジ回帰からのデータ。
