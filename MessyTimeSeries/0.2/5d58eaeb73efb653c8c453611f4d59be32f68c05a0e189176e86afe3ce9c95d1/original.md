```
moving_block_bootstrap(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64, samples::Int64, seed::Int64=1)
```

Generate moving block bootstrap samples.

The moving block bootstrap randomly subsamples a time series into ordered and overlapped blocks of consecutive observations.

# Arguments

  * `Y`: Observed measurements (`nxT`), where `n` and `T` are the number of series and observations.
  * `subsample`: Block size as a percentage of number of observed periods. It is bounded between 0 and 1.
  * `samples`: Number of bootstrap samples.
  * `seed`: Random seed (default: 1).

# References

Kunsch (1989) and Liu and Singh (1992).
