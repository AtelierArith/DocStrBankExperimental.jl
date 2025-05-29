```
NoiseScore
```

ノイズ推定誤差 zスコアデータ構造で、いくつかの予測された [`Merit`](@ref) に関する [`NoiseError`](@ref) の zスコアを含みます。

# フィールド

  * `gls_z_score::Float64`: 一般化最小二乗法 zスコア。
  * `gls_proj_z_score::Float64`: 一般化最小二乗法投影 zスコア。
  * `gls_marginal_z_score::Float64`: 一般化最小二乗法限界 zスコア。
  * `gls_proj_marginal_z_score::Float64`: 一般化最小二乗法投影限界 zスコア。
  * `gls_relative_z_score::Float64`: 一般化最小二乗法相対 zスコア。
  * `gls_proj_relative_z_score::Float64`: 一般化最小二乗法投影相対 zスコア。
  * `wls_z_score::Float64`: 加重最小二乗法 zスコア。
  * `wls_proj_z_score::Float64`: 加重最小二乗法投影 zスコア。
  * `wls_marginal_z_score::Float64`: 加重最小二乗法限界 zスコア。
  * `wls_proj_marginal_z_score::Float64`: 加重最小二乗法投影限界 zスコア。
  * `wls_relative_z_score::Float64`: 加重最小二乗法相対 zスコア。
  * `wls_proj_relative_z_score::Float64`: 加重最小二乗法投影相対 zスコア。
  * `ols_z_score::Float64`: 普通最小二乗法 zスコア。
  * `ols_proj_z_score::Float64`: 普通最小二乗法投影 zスコア。
  * `ols_marginal_z_score::Float64`: 普通最小二乗法限界 zスコア。
  * `ols_proj_marginal_z_score::Float64`: 普通最小二乗法投影限界 zスコア。
  * `ols_relative_z_score::Float64`: 普通最小二乗法相対 zスコア。
  * `ols_proj_relative_z_score::Float64`: 普通最小二乗法投影相対 zスコア。
