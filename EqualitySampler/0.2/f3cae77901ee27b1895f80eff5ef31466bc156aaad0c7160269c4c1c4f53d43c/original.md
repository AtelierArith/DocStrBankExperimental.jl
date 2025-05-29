```
BetaBinomialPartitionDistribution{T <: Integer} <: AbstractPartitionDistribution{T}
```

Beta binomial distribution over partitions. If $\rho \sim \text{BetaBinomialPartitionDistribution}(k, \alpha, \beta)$ then $\text{count\_parameters}(\rho) \sim \text{BetaBinomial}(k - 1, \alpha, \beta)$.
