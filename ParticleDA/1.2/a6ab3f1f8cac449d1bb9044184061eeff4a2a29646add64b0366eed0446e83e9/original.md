```
MeanAndVarSummaryStat <: AbstractCustomReductionSummaryStat
```

Custom reduction based summary statistic type which computes the means and variances o the particle ensemble for each state dimension. On CPU architectures which do not support custom reductions [`NaiveMeanAndVarSummaryStat`](@ref) can be used instead.
