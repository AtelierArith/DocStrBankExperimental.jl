```
SamplingAM(; kwargs...)
```

ユーザーが提供した事前分布から候補をサンプリングし、最も高い獲得値を持つサンプルを返すことで、獲得関数を最適化します。

# キーワード

  * `x_prior::MultivariateDistribution`: 候補をサンプリングするために使用される入力領域の事前分布。
  * `samples::Int`: 引き出され評価されるサンプルの数。
  * `parallel::Bool`: `parallel=true`の場合、サンプリングは並列化されます。デフォルトは`true`です。
