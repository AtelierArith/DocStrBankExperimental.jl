```
SlopeChangeResults <: ChangesResults
```

A struct containing the output of [`estimate_changes`](@ref) used with [`SlopeChangeConfig`](@ref). It can be used for further analysis, visualization, or given to [`significant_transitions`](@ref). The only significance type that you can use this with [`significant_transitions`](@ref) is [`SlopeChangeSignificance`](@ref).

It has the following fields that the user may access:

  * `x`: the input timeseries.
  * `t`: the time vector of the input timeseries.
  * `x_indicator`: the indicator timeseries.
  * `t_indicator`: the time vector of the indicator timeseries.
  * `t_change`: the time the slope changes.
  * `fitparams = a, b, c, d`: the fitted linear coefficients, `a + b*t` before `t_change` and `c + d*t` after `t_change`.
