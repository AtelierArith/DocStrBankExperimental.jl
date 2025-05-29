```
block_jackknife(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64)
```

Generate block jackknife (Kunsch, 1989) samples. This implementation is described in Pellegrino (2022).

This technique subsamples a time series dataset by removing, in turn, all the blocks of consecutive observations with a given size.

# Arguments

  * `Y`: Observed measurements (`nxT`), where `n` and `T` are the number of series and observations.
  * `subsample`: Block size as a percentage of number of observed periods. It is bounded between 0 and 1.

# References

Kunsch (1989) and Pellegrino (2022).
