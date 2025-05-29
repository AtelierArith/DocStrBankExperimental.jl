```
NaiveMeanSummaryStat <: AbstractSumReductionSummaryStat
```

Sum reduction based summary statistic type which computes the means of the particle ensemble for each state dimension. The mean is computed by directly accumulating the  sums of the particle values and number of particles on each rank. If custom reductions  are supported by the CPU architecture in use the more numerically stable  [`MeanSummaryStat`](@ref) should be used instead.
