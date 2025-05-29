```
diagnose(setting; alpha = 0.5)
```

回帰設定を診断し、[`dffits`](@ref)、[`dfbetas`](@ref)、[`cooks`](@ref)、および[`hatmatrix`](@ref)を使用して潜在的な外れ値を報告します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `alpha`: Cooks距離のカットオフのためのアルファ値。[`cooksoutliers`](@ref)を参照してください。
