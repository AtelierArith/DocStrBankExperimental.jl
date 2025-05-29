```julia
struct Delta <: Distributions.Sampleable{Distributions.Univariate, Distributions.Discrete}
```

指定されたδ値でデルタ関数を構築します。この分布は常に同じ値を出力します。
