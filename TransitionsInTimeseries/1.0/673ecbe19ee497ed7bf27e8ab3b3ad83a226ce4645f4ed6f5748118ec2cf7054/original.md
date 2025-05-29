```
SlidingWindowResults <: ChangesResults
```

A struct containing the output of [`estimate_changes`](@ref) used with [`SlidingWindowConfig`](@ref). It can be used for further analysis, visualization, or given to [`significant_transitions`](@ref).

It has the following fields that the user may access

  * `x`: the input timeseries.
  * `t`: the time vector of the input timeseries.
  * `x_indicator`, the indicator timeseries (matrix with each column one indicator).
  * `t_indicator`, the time vector of the indicator timeseries.
  * `x_change`, the change metric timeseries (matrix with each column one change metric).
  * `t_change`, the time vector of the change metric timeseries.
  * `config::SlidingWindowConfig`, what was used for the analysis.
