```
artificial_jackknife(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64, max_samples::Int64, seed::Int64=1)
```

Generate artificial jackknife samples as in Pellegrino (2022).

The artificial delete-$d$ jackknife is an extension of the delete-$d$ jackknife for dependent data problems.

  * This technique replaces the actual data removal step with a fictitious deletion, which consists of imposing $d$-dimensional (artificial) patterns of missing observations to the data.
  * This approach does not alter the data order nor destroy the correlation structure.

# Arguments

  * `Y`: Observed measurements (`nxT`), where `n` and `T` are the number of series and observations.
  * `subsample`: $d$ as a percentage of the original sample size. It is bounded between 0 and 1.
  * `max_samples`: If $\binomial{nT,d}$ is too large, `artificial_jackknife` generates `max_samples` jackknife samples.
  * `seed`: Random seed (default: 1).

# References

Pellegrino (2022).
