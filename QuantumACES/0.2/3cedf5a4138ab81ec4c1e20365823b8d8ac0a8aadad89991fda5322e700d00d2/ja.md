```
ScalingFit
```

垂直および水平方向の距離パラメータを持つ回路の実験デザインのためのスケーリングフィットデータで、通常は脱偏極ノイズの下で行われます。

すべてのフィットパラメータは、$p[1] + p[2] * dist + p[3] * dist^2$という二次関数を表します。

# フィールド

  * `N::Vector{Int}`: ゲート固有値の二次フィットパラメータ。
  * `N_model::Function`: ゲート固有値のための二次モデル。
  * `N_marginal::Vector{Int}`: 限界ゲート固有値の二次フィットパラメータ。
  * `N_marginal_model::Function`: 限界ゲート固有値のための二次モデル。
  * `N_relative::Vector{Int}`: 相対ゲート固有値の二次フィットパラメータ。
  * `N_relative_model::Function`: 相対ゲート固有値のための二次モデル。
  * `G::Vector{Int}`: ゲート数の二次フィットパラメータ。
  * `G_model::Function`: ゲート数のための二次モデル。
  * `gls_tr::Vector{Float64}`: 通常のGLSトレースの二次フィットパラメータ。
  * `gls_tr_model::Function`: 通常のGLSトレースのための二次モデル。
  * `gls_tr_sq::Vector{Float64}`: 通常のGLSトレースの二次フィットパラメータ（平方）。
  * `gls_tr_sq_model::Function`: 通常のGLSトレースの平方のための二次モデル。
  * `gls_expectation_model::Function`: 通常のGLS期待値のモデル。
  * `gls_variance_model::Function`: 通常のGLS分散のモデル。
  * `gls_marginal_tr::Vector{Float64}`: 限界GLSトレースの二次フィットパラメータ。
  * `gls_marginal_tr_model::Function`: 限界GLSトレースのための二次モデル。
  * `gls_marginal_tr_sq::Vector{Float64}`: 限界GLSトレースの二次フィットパラメータ（平方）。
  * `gls_marginal_tr_sq_model::Function`: 限界GLSトレースの平方のための二次モデル。
  * `gls_marginal_expectation_model::Function`: 限界GLS期待値のモデル。
  * `gls_marginal_variance_model::Function`: 限界GLS分散のモデル。
  * `gls_relative_tr::Vector{Float64}`: 相対GLSトレースの二次フィットパラメータ。
  * `gls_relative_tr_model::Function`: 相対GLSトレースのための二次モデル。
  * `gls_relative_tr_sq::Vector{Float64}`: 相対GLSトレースの二次フィットパラメータ（平方）。
  * `gls_relative_tr_sq_model::Function`: 相対GLSトレースの平方のための二次モデル。
  * `gls_relative_expectation_model::Function`: 相対GLS期待値のモデル。
  * `gls_relative_variance_model::Function`: 相対GLS分散のモデル。
  * `wls_tr::Vector{Float64}`: 通常のWLSトレースの二次フィットパラメータ。
  * `wls_tr_model::Function`: 通常のWLSトレースのための二次モデル。
  * `wls_tr_sq::Vector{Float64}`: 通常のWLSトレースの二次フィットパラメータ（平方）。
  * `wls_tr_sq_model::Function`: 通常のWLSトレースの平方のための二次モデル。
  * `wls_expectation_model::Function`: 通常のWLS期待値のモデル。
  * `wls_variance_model::Function`: 通常のWLS分散のモデル。
  * `wls_marginal_tr::Vector{Float64}`: 限界WLSトレースの二次フィットパラメータ。
  * `wls_marginal_tr_model::Function`: 限界WLSトレースのための二次モデル。
  * `wls_marginal_tr_sq::Vector{Float64}`: 限界WLSトレースの二次フィットパラメータ（平方）。
  * `wls_marginal_tr_sq_model::Function`: 限界WLSトレースの平方のための二次モデル。
  * `wls_marginal_expectation_model::Function`: 限界WLS期待値のモデル。
  * `wls_marginal_variance_model::Function`: 限界WLS分散のモデル。
  * `wls_relative_tr::Vector{Float64}`: 相対WLSトレースの二次フィットパラメータ。
  * `wls_relative_tr_model::Function`: 相対WLSトレースのための二次モデル。
  * `wls_relative_tr_sq::Vector{Float64}`: 相対WLSトレースの二次フィットパラメータ（平方）。
  * `wls_relative_tr_sq_model::Function`: 相対WLSトレースの平方のための二次モデル。
  * `wls_relative_expectation_model::Function`: 相対WLS期待値のモデル。
  * `wls_relative_variance_model::Function`: 相対WLS分散のモデル。
  * `ols_tr::Vector{Float64}`: 通常のOLSトレースの二次フィットパラメータ。
  * `ols_tr_model::Function`: 通常のOLSトレースのための二次モデル。
  * `ols_tr_sq::Vector{Float64}`: 通常のOLSトレースの二次フィットパラメータ（平方）。
  * `ols_tr_sq_model::Function`: 通常のOLSトレースの平方のための二次モデル。
  * `ols_expectation_model::Function`: 通常のOLS期待値のモデル。
  * `ols_variance_model::Function`: 通常のOLS分散のモデル。
  * `ols_marginal_tr::Vector{Float64}`: 限界OLSトレースの二次フィットパラメータ。
  * `ols_marginal_tr_model::Function`: 限界OLSトレースのための二次モデル。
  * `ols_marginal_tr_sq::Vector{Float64}`: 限界OLSトレースの二次フィットパラメータ（平方）。
  * `ols_marginal_tr_sq_model::Function`: 限界OLSトレースの平方のための二次モデル。
  * `ols_marginal_expectation_model::Function`: 限界OLS期待値のモデル。
  * `ols_marginal_variance_model::Function`: 限界OLS分散のモデル。
  * `ols_relative_tr::Vector{Float64}`: 相対OLSトレースの二次フィットパラメータ。
  * `ols_relative_tr_model::Function`: 相対OLSトレースのための二次モデル。
  * `ols_relative_tr_sq::Vector{Float64}`: 相対OLSトレースの二次フィットパラメータ（平方）。
  * `ols_relative_tr_sq_model::Function`: 相対OLSトレースの平方のための二次モデル。
  * `ols_relative_expectation_model::Function`: 相対OLS期待値のモデル。
  * `ols_relative_variance_model::Function`: 相対OLS分散のモデル。
