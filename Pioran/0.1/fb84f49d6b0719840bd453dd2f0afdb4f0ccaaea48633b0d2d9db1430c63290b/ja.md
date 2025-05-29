```
run_posterior_predict_checks(samples, paramnames, t, y, yerr, f0, fM, model, with_log_transform; plots="all", n_samples=200, path="", basis_function="SHO", n_frequencies=1000, plot_f_P=false, n_components=20)
```

モデルとPSDの近似のための事後予測チェックを実行します

# 引数

  * `samples::Array{Float64, 2}` : 事後分布からのサンプル
  * `paramnames::Array{String, 1}` : パラメータの名前
  * `t::Array{Float64, 1}` : 時系列
  * `y::Array{Float64, 1}` : 時系列の値
  * `yerr::Array{Float64, 1}` : 時系列の誤差
  * `f0::Float64` : PSDの近似のための最小周波数
  * `fM::Float64` : PSDの近似のための最大周波数
  * `model::Function` : モデル
  * `with_log_transform::Bool` : trueの場合、フラックスは対数変換されます
  * `plots::String or Array{String, 1}` : 作成するプロットの種類。 "all"、"psd"、"lsp"、"timeseries"、またはそれらの組み合わせを配列で指定できます
  * `n_samples::Int=200` : 事後予測分布から引き出すサンプルの数
  * `path::String="all"` : プロットを保存するパス
  * `basis_function::String="SHO"` : PSDの近似のための基底関数
  * `n_frequencies::Int=1000` : PSDの近似のために使用する周波数の数
  * `plot_f_P::Bool=false` : trueの場合、プロットはf * PSDの観点で作成されます
  * `n_components::Int=20` : PSDの近似のために使用するコンポーネントの数
