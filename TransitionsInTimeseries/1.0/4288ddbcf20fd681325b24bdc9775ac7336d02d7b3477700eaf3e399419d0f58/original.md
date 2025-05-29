```
SegmentedWindowConfig <: IndicatorsChangeConfig
SegmentedWindowConfig(indicators, change_metrics, tseg_start, tseg_end; kwargs...)
```

A configuration that can be given to [`estimate_changes`](@ref). It estimates transitions by estimating indicators and changes in user-defined window segments as follows:

1. For each segment specified, estimate the corresponding indicator timeseries by sliding a window over the input timeseries (within the window segment).
2. For each segment of the indicator timeseries, estimate a scalar change metric by applying the change metric over the full segment of the indicator timeseries.d

`tseg_start, tseg_end` are the starts and ends of the window segments (the window segments may overlap, that's okay). `indicators, change_metrics` are identical as in [`SlidingWindowConfig`](@ref).

The results output corresponding to `SlidingWindowConfig` is [`SegmentedWindowResults`](@ref).

## Keyword arguments

  * `width_ind::Int=100, stride_ind::Int=1, whichtime = midpoint, T = Float64`: keywords identical as in [`SlidingWindowConfig`](@ref).
  * `min_width_cha::Int=typemax(Int)`: minimal width required to perform the change metric estimation. If a segment is not sufficiently long, the change metric is `NaN`.
