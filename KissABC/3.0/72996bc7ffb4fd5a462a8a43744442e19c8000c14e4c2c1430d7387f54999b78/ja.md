```
Factored{N} <: Distribution{Multivariate, MixedSupport}
```

複数の `UnivariateDistribution` を組み合わせてサンプリングするために使用できる `Distribution` タイプです。例: `prior = Factored(Normal(0,1), Uniform(-1,1))` のように使用できます。
