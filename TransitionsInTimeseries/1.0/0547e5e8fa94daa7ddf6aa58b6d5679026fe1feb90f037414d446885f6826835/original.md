```
SegmentedWindowResults <: ChangesResults
```

A struct containing the output of [`estimate_changes`](@ref) used with [`SegmentedWindowConfig`](@ref). It can be used for further analysis, visualization, or given to [`significant_transitions`](@ref).

It has the following fields that the user may access

  * `x`: the input timeseries.
  * `t`: the time vector of the input timeseries.
  * `x_indicator::Vector{Matrix}`, with `x_indicator[k]` the indicator timeseries (matrix  with each column one indicator) of the `k`-th segment.
  * `t_indicator::Vector{Vector}`, with `t_indicator[k]` the time vector of the indicator timeseries for the `k`-th segment.
  * `x_change::Matrix`, the change metric values with `x[k, i]` the change metric of the `i`-th indicator for the `k`-th segment.
  * `t_change`, the time vector of the change metric.
  * `config::SegmentedWindowConfig`, what was used for the analysis.
  * `i1::Vector{Int}` indices corresponding to start time of each segment.
  * `i2::Vector{Int}` indices corresponding to end time of each segment.
  * `precomp_change_metrics` vector containing the precomputed change metrics of each segment.
