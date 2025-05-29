```
PrecomputedCustomInclusionPartitionDistribution(k::T, logpdf::NTuple{N, Float64})
```

PrecomputedCustomInclusionPartitionDistributionはCustomInclusionPartitionDistributionと同じですが、追加で対数期待等価数をキャッシュします。特定のパーティションの対数確率は、したがって、logpdfと対数期待等価数の差になります。この分布は、パーティション確率を繰り返し計算する際（例：MCMC）に推奨されます。
