```
estimate_gate_noise(d::Design, noise_est::NoiseEstimate; kwargs...)
estimate_gate_noise(d_rand::RandDesign, noise_est::NoiseEstimate; kwargs...)
estimate_gate_noise(d::Design, est_eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}, est_covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}, shot_budget::Int; kwargs...)
estimate_gate_noise(d_rand::RandDesign, est_eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}, est_covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}; kwargs...)
```

デザイン `d` またはランダム化デザイン `d_rand` のゲートノイズの [`NoiseEstimate`](@ref) を返します。これは、ノイズ推定 `noise_est` に既に含まれている推定回路固有値、または推定回路固有値 `est_eigenvalues_experiment_ensemble` と共分散回路固有値 `est_covariance_experiment_ensemble` から導出され、ショット予算 `shot_budget` を持ちます。

# 引数

  * `d::Design`: 実験デザイン。
  * `d_rand::RandDesign`: ランダム化実験デザイン。
  * `noise_est::NoiseEstimate`: ノイズ推定。
  * `est_eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: 推定された回路固有値のアンサンブル。
  * `est_covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: 推定された共分散回路固有値のアンサンブル。
  * `shot_budget::Int`: ノイズ推定のショット予算。

# キーワード引数

  * `min_eigenvalue::Float64 = 0.1`: クリッピングのための最小固有値閾値。
  * `clip_warning::Bool = true`: 固有値がクリップされた場合に警告するかどうか。
  * `N_warn_split::Integer = 5 * 10^3`: 警告を出すべきゲート固有値の数。
  * `split::Bool = (d.c.gate_data.N < N_warn_split ? false : true)`: ゲート固有値の投影をゲート間で分割するか、すべてのゲート固有値を同時に投影するか。
  * `split_warning::Bool = true`: ゲート固有値の投影が分割されていない場合に警告するかどうか。
  * `precision::Real = 1e-8`: ゲート固有値の投影のためのソルバの精度。
