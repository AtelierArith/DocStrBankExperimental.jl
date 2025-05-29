```
MeanSummaryStat <: AbstractCustomReductionSummaryStat
```

Custom reduction based summary statistic type which computes the means of the particle ensemble for each state dimension. On CPU architectures which do not support custom reductions [`NaiveMeanSummaryStat`](@ref) can be used instead.
