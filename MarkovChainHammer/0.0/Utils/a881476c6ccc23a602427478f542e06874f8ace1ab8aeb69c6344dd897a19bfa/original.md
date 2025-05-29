```
autocovariance(x; timesteps=length(x), progress = false)
```

Calculate the autocovariance of a timeseries `x` with `timesteps` lags.

# Arguments

  * `x::AbstractVector`: timeseries

# Keyword Arguments

  * `timesteps::Int`: number of lags
  * `progress::Bool`: show a progress bar

# Returns

  * `autocov::Vector`: autocovariance of `x` with `timesteps` lags
