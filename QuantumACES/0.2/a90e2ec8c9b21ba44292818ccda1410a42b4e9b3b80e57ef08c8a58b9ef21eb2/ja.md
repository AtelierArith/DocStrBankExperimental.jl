```
NoiseError
```

正規化平方根平均二乗誤差 (NRMSE) を含むノイズ推定エラーデータ構造 [`NoiseEstimate`](@ref) のための。

# フィールド

  * `gls_nrmse::Float64`: 一般化最小二乗法の正規化平方根平均二乗誤差。
  * `gls_proj_nrmse::Float64`: 一般化最小二乗法の投影正規化平方根平均二乗誤差。
  * `gls_marginal_nrmse::Float64`: 一般化最小二乗法の周辺正規化平方根平均二乗誤差。
  * `gls_proj_marginal_nrmse::Float64`: 一般化最小二乗法の投影周辺正規化平方根平均二乗誤差。
  * `gls_relative_nrmse::Float64`: 一般化最小二乗法の相対正規化平方根平均二乗誤差。
  * `gls_proj_relative_nrmse::Float64`: 一般化最小二乗法の投影相対正規化平方根平均二乗誤差。
  * `wls_nrmse::Float64`: 加重最小二乗法の正規化平方根平均二乗誤差。
  * `wls_proj_nrmse::Float64`: 加重最小二乗法の投影正規化平方根平均二乗誤差。
  * `wls_marginal_nrmse::Float64`: 加重最小二乗法の周辺正規化平方根平均二乗誤差。
  * `wls_proj_marginal_nrmse::Float64`: 加重最小二乗法の投影周辺正規化平方根平均二乗誤差。
  * `wls_relative_nrmse::Float64`: 加重最小二乗法の相対正規化平方根平均二乗誤差。
  * `wls_proj_relative_nrmse::Float64`: 加重最小二乗法の投影相対正規化平方根平均二乗誤差。
  * `ols_nrmse::Float64`: 通常の最小二乗法の正規化平方根平均二乗誤差。
  * `ols_proj_nrmse::Float64`: 通常の最小二乗法の投影正規化平方根平均二乗誤差。
  * `ols_marginal_nrmse::Float64`: 通常の最小二乗法の周辺正規化平方根平均二乗誤差。
  * `ols_proj_marginal_nrmse::Float64`: 通常の最小二乗法の投影周辺正規化平方根平均二乗誤差。
  * `ols_relative_nrmse::Float64`: 通常の最小二乗法の相対正規化平方根平均二乗誤差。
  * `ols_proj_relative_nrmse::Float64`: 通常の最小二乗法の投影相対正規化平方根平均二乗誤差。
