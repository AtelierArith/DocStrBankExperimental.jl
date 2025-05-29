```
constrain(pop::UncertainScalarPopulation, constraint::SamplingConstraint, n::Int = 30000)
```

与えられたサンプリング `constraint` によって `UncertainScalarPopulation` を制約します。サンプリング制約が計算のために再サンプリングを必要とする場合、`n` 回再サンプリングします。
