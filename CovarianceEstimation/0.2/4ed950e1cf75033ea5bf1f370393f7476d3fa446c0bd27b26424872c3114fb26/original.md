```
cov(lse::LinearShrinkage, X, [weights::FrequencyWeights]; dims=1, mean=nothing)
```

Linear shrinkage covariance estimator for matrix `X` along dimension `dims`. Computed using the method described by `lse`.

Optionally provide `weights` associated with each observation in `X` (see `StatsBase.FrequencyWeights`).

!!! note
    Theoretical guidance for the use of weights in shrinkage estimation seems sparse. `FrequencyWeights` have a straightforward implementation, but support for other `AbstractWeight` subtypes awaits analytical justification.

