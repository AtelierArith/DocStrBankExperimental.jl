```
PrecomputedCustomInclusionPartitionDistribution(k::T, logpdf::NTuple{N, Float64})
```

PrecomputedCustomInclusionPartitionDistribution is identical to CustomInclusionPartitionDistribution, but additionally caches the log expected equality counts. The log probability of a particular partition is thus the difference between the logpdf and the log expected equality counts. This distribution is recommended when repeatedly computing partition probabilities (e.g., in MCMC).
