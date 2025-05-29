```
time_series([rng=Random.GLOBAL_RNG,] ld, ts_length, init_actions)
```

Return a time series of action profiles.

# Arguments

  * `rng::AbstractRNG` : Random number generator used.
  * `ld::LogitDynamics{N}` : `LogitDynamics` instance.
  * `ts_length::Integer` : The length of time series.
  * `init_actions::PureActionProfile` : Initial action profile.

# Returns

  * `::Matrix{<:Integer}` : The time series of action profiles.
