```
GridSearchResult{TF<:AbstractFloat} <: ModelSelectionResult
```

[`GridSearch`](@ref) によって計算された各パラメータの推定値を含む追加結果。

# フィールド

  * `iopt::Dict{SearchCriterion,Int}`: 各基準に基づく最適パラメータのインデックス。
  * `θs::Matrix{TF}`: 得られた点推定値。
  * `loocv::Vector{TF}`: 一つを除いた交差検証誤差。
  * `rss::Vector{TF}`: 残差平方和。
  * `gcv::Vector{TF}`: 一般化交差検証誤差。
  * `aic::Vector{TF}`: 赤池情報量基準値。
  * `dof_fit::Vector{TF}`: フィットの自由度。
  * `dof_res::Vector{TF}`: 残差の自由度。
