```
BetaBinomialPartitionDistribution{T <: Integer} <: AbstractPartitionDistribution{T}
```

パーティションに対するベータ二項分布。もし $\rho \sim \text{BetaBinomialPartitionDistribution}(k, \alpha, \beta)$ ならば、 $\text{count\_parameters}(\rho) \sim \text{BetaBinomial}(k - 1, \alpha, \beta)$ です。
