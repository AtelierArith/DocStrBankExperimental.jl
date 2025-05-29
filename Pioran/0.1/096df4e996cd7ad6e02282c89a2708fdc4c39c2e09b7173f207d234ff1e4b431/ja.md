```
run_diagnostics(prior_samples, variance_samples, f0, fM, model, f_min, f_max; path="", basis_function="SHO", n_components=20)
```

モデルの事前予測チェックとPSDの近似を実行します

# 引数

  * `prior_samples::Array{Float64, 2}` : 事前分布からのモデルサンプル
  * `variance_samples::Array{Float64, 1}` : 分散サンプル
  * `f0::Float64` : PSDの近似のための最小周波数
  * `fM::Float64` : PSDの近似のための最大周波数
  * `model::Function` : モデル
  * `f_min::Float64` : 観測データの最小周波数
  * `f_max::Float64` : 観測データの最大周波数
  * `path::String=""` : プロットを保存するパス
  * `basis_function::String="SHO"` : PSDの近似のための基底関数
  * `n_components::Int=20` : PSDの近似に使用するコンポーネントの数
