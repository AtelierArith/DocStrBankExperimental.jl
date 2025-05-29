```
NonlinModel(; kwargs...)
```

パラメトリックサロゲモデル。

モデルが線形の場合は、将来的により良いパフォーマンスを提供する`LinModel`を使用できます。（まだ実装されていません。）

モデルを`y = predict(x, θ)`として定義します。ここで、`θ`はモデルパラメータです。

# キーワード

  * `predict::Function`: 上記の定義に従った`predict`関数。
  * `theta_priors::AbstractVector{<:UnivariateDistribution}`: モデルパラメータの事前分布。
  * `noise_std_priors::NoiseStdPriors`: 各`y`次元のノイズ標準偏差の事前分布。
