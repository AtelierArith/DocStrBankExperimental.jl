```
sample_approx_model(samples, variance_samples, f0, fM, model; n_frequencies=1_000, basis_function="SHO", n_components=20)
```

PSDの近似を確認するために、残差とPSDおよび近似PSDの比率を計算します。

# 引数

  * `samples::Array{Float64, n}` : モデルサンプル
  * `variance_samples::Array{Float64, 1}` : 分散サンプル
  * `f0::Float64` : PSDの近似のための最小周波数
  * `fM::Float64` : PSDの近似のための最大周波数
  * `model::Function` : モデル
  * `n_frequencies::Int=1_000` : PSDの近似に使用する周波数の数
  * `basis_function::String="SHO"` : PSDの近似のための基底関数
  * `n_components::Int=20` : PSDの近似に使用するコンポーネントの数

# 戻り値

  * `psd::Array{Float64, 2}` : PSD
  * `psd_approx::Array{Float64, 2}` : 近似PSD
  * `residuals::Array{Float64, 2}` : 残差 (psd-approx_psd)
  * `ratios::Array{Float64, 2}` : 比率 (approx_psd/psd)
