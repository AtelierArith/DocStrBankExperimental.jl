```julia
TikTak(quasirandom_N; keep_ratio, θ_min, θ_max, θ_pow)

```

「TikTak」マルチスタート法は、*Arnoud, Guvenen, and Kleineberg (2019)*で説明されています。

これは*マルチスタート*部分を実装しており、任意のローカルメソッドで呼び出すことができます。 [`multistart_minimization`](@ref)を参照してください。

# 引数

  * `quasirandom_N`: 最初のパスのための準ランダム点の数（Sobol列を使用）。

# キーワード引数

  * `keep_ratio`: 保持される最良の準ランダム点の割合
  * `θ_min`と`θ_max`は重みパラメータを制限し、`θ_pow`はそれが上昇するべき累乗を決定します。

デフォルトは上記の論文からのものです。
