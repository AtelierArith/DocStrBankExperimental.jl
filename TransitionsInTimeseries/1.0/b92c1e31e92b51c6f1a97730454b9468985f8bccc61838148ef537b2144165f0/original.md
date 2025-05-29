```
SlidingWindowConfig <: ChangesConfig
SlidingWindowConfig(indicators, change_metrics; kwargs...)
```

A configuration that can be given to [`estimate_changes`](@ref). It estimates transitions by a sliding window approach:

1. Estimate the timeseries of an indicator by sliding a window over the input timeseries.
2. Estimate changes of an indicator by sliding a window of the change metric over the indicator timeseries.

Both indicators and change metrics are **generic Julia functions** that input an `x::AbstractVector` and output an `s::Real`. Any function may be given and see [making custom indicators/change metrics](@ref own_indicator) in the documentation for more information on possible optimizations.

`indicators` can be a single function or a tuple of indicators. Similarly, `change_metrics` can be a tuple or a single function. If tuples, the length of `indicators` and `change_metrics` must match. This way the analysis can be efficiently repeated for many indicators and/or change metrics.

The results output corresponding to `SlidingWindowConfig` is [`SlidingWindowResults`](@ref).

Step 1. is skipped if `nothing` is provided as `indicators`, in which case the change metrics are estimated directly from input data.

## Keyword arguments

  * `width_ind::Int=100, stride_ind::Int=1`: width and stride given to [`WindowViewer`](@ref) to compute the indicator from the input timeseries.
  * `width_cha::Int=50, stride_cha::Int=1`: width and stride given to [`WindowViewer`](@ref) to compute the change metric timeseries from the indicator timeseries.
  * `whichtime = midpoint`: The time vector corresponding to the indicators / change metric timeseries is obtained from `t` in [`estimate_changes`](@ref) using the keyword `whichtime`. Options include:

      * `last`: use the last timepoint of each window
      * `midpoint`: use the mid timepoint of each time window
      * `first`: use first timepoint of each window

    In fact, the indicators time vector is computed simply via

    ```julia
    t_indicator = windowmap(whichtime, t; width_ind, stride_ind)
    t_change = windowmap(whichtime, t_indicator; width_cha, stride_cha)
    ```

    so any other function of the time window may be given to extract the time point itself, such as `mean` or `median`.
  * `T = Float64`: Element type of input timeseries to initialize some computations.
