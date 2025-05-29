Supertype for forecast time series Current concrete subtypes are:

  * [`Deterministic`](@ref)
  * [`DeterministicSingleTimeSeries`](@ref)
  * [`Scenarios`](@ref)
  * [`Probabilistic`](@ref)

Subtypes of Forecast must implement:

  * `get_horizon_count`
  * `get_initial_times`
  * `get_initial_timestamp`
  * `get_name`
  * `get_scaling_factor_multiplier`
  * `get_window`
  * `iterate_windows`
