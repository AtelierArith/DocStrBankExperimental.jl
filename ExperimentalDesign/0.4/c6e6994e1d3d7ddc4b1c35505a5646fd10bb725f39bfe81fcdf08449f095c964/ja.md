```julia
struct CategoricalFactor <: Distributions.Distribution{Distributions.Univariate, Distributions.Discrete}
```

  * `values::Vector`
  * `distribution::Distributions.DiscreteUniform`

非数値配列に対する `DiscreteUniform` 分布のシンプルなラッパーです。
