```
アンサンブルフィット
```

アンサンブルスケーリングフィットデータは、ランダムノイズモデルの下での垂直および水平方向の距離パラメータを持つ回路の実験デザインのためのものです。

すべてのペアフィットパラメータは、期待値と分散の式に現れるトレースおよびトレースの二乗の二次項に対応しています。

# フィールド

  * `gls_pair::Vector{Float64}`: 通常のGLSペア二次フィットパラメータ。
  * `gls_expectation_model::Function`: 通常のGLS期待値のモデル。
  * `gls_variance_model::Function`: 通常のGLS分散のモデル。
  * `gls_marginal_pair::Vector{Float64}`: マージナルGLSペア二次フィットパラメータ。
  * `gls_marginal_expectation_model::Function`: マージナルGLS期待値のモデル。
  * `gls_marginal_variance_model::Function`: マージナルGLS分散のモデル。
  * `gls_relative_pair::Vector{Float64}`: 相対GLSペア二次フィットパラメータ。
  * `gls_relative_expectation_model::Function`: 相対GLS期待値のモデル。
  * `gls_relative_variance_model::Function`: 相対GLS分散のモデル。
  * `wls_pair::Vector{Float64}`: 通常のWLSペア二次フィットパラメータ。
  * `wls_expectation_model::Function`: 通常のWLS期待値のモデル。
  * `wls_variance_model::Function`: 通常のWLS分散のモデル。
  * `wls_marginal_pair::Vector{Float64}`: マージナルWLSペア二次フィットパラメータ。
  * `wls_marginal_expectation_model::Function`: マージナルWLS期待値のモデル。
  * `wls_marginal_variance_model::Function`: マージナルWLS分散のモデル。
  * `wls_relative_pair::Vector{Float64}`: 相対WLSペア二次フィットパラメータ。
  * `wls_relative_expectation_model::Function`: 相対WLS期待値のモデル。
  * `wls_relative_variance_model::Function`: 相対WLS分散のモデル。
  * `ols_pair::Vector{Float64}`: 通常のOLSペア二次フィットパラメータ。
  * `ols_expectation_model::Function`: 通常のOLS期待値のモデル。
  * `ols_variance_model::Function`: 通常のOLS分散のモデル。
  * `ols_marginal_pair::Vector{Float64}`: マージナルOLSペア二次フィットパラメータ。
  * `ols_marginal_expectation_model::Function`: マージナルOLS期待値のモデル。
  * `ols_marginal_variance_model::Function`: マージナルOLS分散のモデル。
  * `ols_relative_pair::Vector{Float64}`: 相対OLSペア二次フィットパラメータ。
  * `ols_relative_expectation_model::Function`: 相対OLS期待値のモデル。
  * `ols_relative_variance_model::Function`: 相対OLS分散のモデル。
