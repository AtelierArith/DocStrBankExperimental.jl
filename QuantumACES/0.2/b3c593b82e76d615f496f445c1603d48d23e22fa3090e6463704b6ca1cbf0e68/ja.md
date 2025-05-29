```
NoiseEstimate
```

ノイズ推定データ構造。

# フィールド

  * `eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: 各タプルおよび回路固有値の回路固有値推定。
  * `covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: 各タプルおよび共分散回路固有値の共分散回路固有値推定。
  * `shot_budget::Int`: （潜在的にランダム化された）実験アンサンブルのショット予算。
  * `gls_unproj_gate_eigenvalues::Vector{Float64}`: 一般化最小二乗法の未投影ゲート固有値。
  * `gls_gate_eigenvalues::Vector{Float64}`: 一般化最小二乗法の投影ゲート固有値。
  * `gls_unproj_gate_probabilities::Dict{Gate, Vector{Float64}}`: 一般化最小二乗法の未投影ゲート誤差確率。
  * `gls_gate_probabilities::Dict{Gate, Vector{Float64}}`: 一般化最小二乗法の投影ゲート誤差確率。
  * `gls_unproj_marginal_gate_eigenvalues::Vector{Float64}`: 一般化最小二乗法の未投影周辺ゲート固有値。
  * `gls_marginal_gate_eigenvalues::Vector{Float64}`: 一般化最小二乗法の投影周辺ゲート固有値。
  * `gls_unproj_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 一般化最小二乗法の未投影周辺ゲート誤差確率。
  * `gls_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 一般化最小二乗法の投影周辺ゲート誤差確率。
  * `gls_unproj_relative_gate_eigenvalues::Vector{Float64}`: 一般化最小二乗法の未投影相対ゲート固有値。
  * `gls_relative_gate_eigenvalues::Vector{Float64}`: 一般化最小二乗法の投影相対ゲート固有値。
  * `wls_unproj_gate_eigenvalues::Vector{Float64}`: 加重最小二乗法の未投影ゲート固有値。
  * `wls_gate_eigenvalues::Vector{Float64}`: 加重最小二乗法の投影ゲート固有値。
  * `wls_unproj_gate_probabilities::Dict{Gate, Vector{Float64}}`: 加重最小二乗法の未投影ゲート誤差確率。
  * `wls_gate_probabilities::Dict{Gate, Vector{Float64}}`: 加重最小二乗法の投影ゲート誤差確率。
  * `wls_unproj_marginal_gate_eigenvalues::Vector{Float64}`: 加重最小二乗法の未投影周辺ゲート固有値。
  * `wls_marginal_gate_eigenvalues::Vector{Float64}`: 加重最小二乗法の投影周辺ゲート固有値。
  * `wls_unproj_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 加重最小二乗法の未投影周辺ゲート誤差確率。
  * `wls_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 加重最小二乗法の投影周辺ゲート誤差確率。
  * `wls_unproj_relative_gate_eigenvalues::Vector{Float64}`: 加重最小二乗法の未投影相対ゲート固有値。
  * `wls_relative_gate_eigenvalues::Vector{Float64}`: 加重最小二乗法の投影相対ゲート固有値。
  * `ols_unproj_gate_eigenvalues::Vector{Float64}`: 普通の最小二乗法の未投影ゲート固有値。
  * `ols_gate_eigenvalues::Vector{Float64}`: 普通の最小二乗法の投影ゲート固有値。
  * `ols_unproj_gate_probabilities::Dict{Gate, Vector{Float64}}`: 普通の最小二乗法の未投影ゲート誤差確率。
  * `ols_gate_probabilities::Dict{Gate, Vector{Float64}}`: 普通の最小二乗法の投影ゲート誤差確率。
  * `ols_unproj_marginal_gate_eigenvalues::Vector{Float64}`: 普通の最小二乗法の未投影周辺ゲート固有値。
  * `ols_marginal_gate_eigenvalues::Vector{Float64}`: 普通の最小二乗法の投影周辺ゲート固有値。
  * `ols_unproj_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 普通の最小二乗法の未投影周辺ゲート誤差確率。
  * `ols_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 普通の最小二乗法の投影周辺ゲート誤差確率。
  * `ols_unproj_relative_gate_eigenvalues::Vector{Float64}`: 普通の最小二乗法の未投影相対ゲート固有値。
  * `ols_relative_gate_eigenvalues::Vector{Float64}`: 普通の最小二乗法の投影相対ゲート固有値。
