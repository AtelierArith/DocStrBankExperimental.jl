```
GaussianProcess(; kwargs...)
```

ガウス過程サロゲートモデル。各出力次元は別々の独立したプロセスによってモデル化されます。

# キーワード

  * `mean::Union{Nothing, Function}`: GPの平均関数として使用されます。デフォルトは`nothing`で、`x -> zeros(y_dim)`に相当します。
  * `kernel::Kernel`: GPで使用されるカーネル。デフォルトは`Matern32Kernel()`です。
  * `length_scale_priors::LengthScalePriors`: GPの長さスケールの事前分布。`length_scale_priors`は、`x_dim`と`y_dim`がそれぞれモデルの入力と出力の次元である`y_dim`の`x_dim`変量分布のベクトルである必要があります。
  * `amp_priors::AmplitudePriors`: GPの振幅ハイパーパラメータの事前分布。`amp_priors`は、`y_dim`の単変量分布のベクトルである必要があります。
  * `noise_std_priors::NoiseStdPriors`: 各`y`次元のノイズ標準偏差の事前分布。
