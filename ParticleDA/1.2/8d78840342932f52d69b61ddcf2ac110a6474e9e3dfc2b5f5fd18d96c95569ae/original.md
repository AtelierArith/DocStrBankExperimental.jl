```
NaiveMeanAndVarSummaryStat <: AbstractSumReductionSummaryStat
```

Sum reduction based summary statistic type which computes the means and variances of the particle ensemble for each state dimension. The mean and variance are computed by directly accumulating the  sums of the particle values, the squared particle values and number of particles on each rank, with the variance computed as the scaled difference between the sum of the squares and square of the sums. This 'naive' implementation avoids custom MPI reductions but can be numerically unstable for large ensembles or state components with large values. If custom reductions are supported by the CPU architecture in use the more numerically stable [`MeanAndVarSummaryStat`](@ref) should be used instead.
