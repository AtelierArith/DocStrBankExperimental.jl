```
stationary_block_bootstrap(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64, samples::Int64, seed::Int64=1)
```

Generate stationary block bootstrap samples.

The stationary bootstrap is similar to the block bootstrap proposed in independently in Kunsch (1989) and Liu and Singh (1992).

There are two main differences:

  * The blocks have random length
  * In order to achieve stationarity, the stationary (block) bootstrap "wraps" the data around in a "circle" so that the first observation follows the last.

Note: Block size is exponentially distributed with mean `Int64(ceil(subsample*T))`.

# Arguments

  * `Y`: Observed measurements (`nxT`), where `n` and `T` are the number of series and observations.
  * `subsample`: Block size as a percentage of number of observed periods. It is bounded between 0 and 1.
  * `samples`: Number of bootstrap samples.
  * `seed`: Random seed (default: 1).

# References

Politis and Romano (1994).
