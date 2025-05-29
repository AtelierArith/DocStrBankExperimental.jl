```
Merit
```

実験デザインのためのメリットパラメータ。

# フィールド

  * `circuit_param::AbstractCircuitParameters`: 回路パラメータ。
  * `noise_param::AbstractNoiseParameters`: ノイズパラメータ。
  * `tuple_set_data::TupleSetData`: [`TupleSetData`](@ref) オブジェクトで、タプルセットを生成します。
  * `tuple_times::Vector{Float64}`: 基本タプルセットに従って正規化された各タプルに対応する回路を実装するのにかかる時間。
  * `shot_weights::Vector{Float64}`: セット内の各タプルのショットウェイトで、合計は1になります。
  * `experiment_numbers::Vector{Int}`: セット内の各タプルの実験数。
  * `experiment_number::Int`: 実験の総数。
  * `N::Int`: ゲートの固有値の数。
  * `N_marginal::Int`: 限界ゲートの固有値の数。
  * `N_relative::Int`: 相対精度の限界ゲートの固有値の数。
  * `G::Int`: ゲートの総数。
  * `gls_expectation::Float64`: 一般化最小二乗法（GLS）ゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `gls_variance::Float64`: GLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `gls_cov_eigenvalues::Vector{Float64}`: GLSゲート固有値推定器共分散行列の固有値。
  * `gls_marginal_expectation::Float64`: 限界GLSゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `gls_marginal_variance::Float64`: 限界GLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `gls_marginal_cov_eigenvalues::Vector{Float64}`: 限界GLSゲート固有値推定器共分散行列の固有値。
  * `gls_relative_expectation::Float64`: 相対精度の限界GLSゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `gls_relative_variance::Float64`: 相対精度の限界GLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `gls_relative_cov_eigenvalues::Vector{Float64}`: 相対精度の限界GLSゲート固有値推定器共分散行列の固有値。
  * `wls_expectation::Float64`: 加重最小二乗法（WLS）ゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `wls_variance::Float64`: WLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `wls_cov_eigenvalues::Vector{Float64}`: WLSゲート固有値推定器共分散行列の固有値。
  * `wls_marginal_expectation::Float64`: 限界WLSゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `wls_marginal_variance::Float64`: 限界WLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `wls_marginal_cov_eigenvalues::Vector{Float64}`: 限界WLSゲート固有値推定器共分散行列の固有値。
  * `wls_relative_expectation::Float64`: 相対精度の限界WLSゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `wls_relative_variance::Float64`: 相対精度の限界WLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `wls_relative_cov_eigenvalues::Vector{Float64}`: 相対精度の限界WLSゲート固有値推定器共分散行列の固有値。
  * `ols_expectation::Float64`: 普通の最小二乗法（OLS）ゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `ols_variance::Float64`: OLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `ols_cov_eigenvalues::Vector{Float64}`: OLSゲート固有値推定器共分散行列の固有値。
  * `ols_marginal_expectation::Float64`: 限界OLSゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `ols_marginal_variance::Float64`: 限界OLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `ols_marginal_cov_eigenvalues::Vector{Float64}`: 限界OLSゲート固有値推定器共分散行列の固有値。
  * `ols_relative_expectation::Float64`: 相対精度の限界OLSゲート固有値推定器ベクトルの期待される正規化RMS誤差。
  * `ols_relative_variance::Float64`: 相対精度の限界OLSゲート固有値推定器ベクトルの正規化RMS誤差の分散。
  * `ols_relative_cov_eigenvalues::Vector{Float64}`: 相対精度の限界OLSゲート固有値推定器共分散行列の固有値。
  * `cond_num::Float64`: 設計行列の条件数、最大および最小の特異値の比。
  * `pinv_norm::Float64`: 設計行列の擬似逆行列のノルム、最小の特異値の逆数。
