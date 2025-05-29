予測時系列のスーパタイプ 現在の具体的なサブタイプは次のとおりです：

  * [`Deterministic`](@ref)
  * [`DeterministicSingleTimeSeries`](@ref)
  * [`Scenarios`](@ref)
  * [`Probabilistic`](@ref)

Forecastのサブタイプは次のメソッドを実装する必要があります：

  * `get_horizon_count`
  * `get_initial_times`
  * `get_initial_timestamp`
  * `get_name`
  * `get_scaling_factor_multiplier`
  * `get_window`
  * `iterate_windows`
