```
SlopeChangeConfig <: ChangesConfig
SlopeChangeConfig(; indicator = nothing, kw...)
```

A configuration that can be given to [`estimate_changes`](@ref). It estimates a change of slope in the timeseries by fitting two connected linear segments to the timeseries, returning the results (i.e., the two-linear fits) as [`SlopeChangeResults`](@ref).

Currently, significance of `SlopeChangeConfig` results can only be checked with [`SlopeChangeSignificance`](@ref).

## Keyword arguments

  * `indicator = nothing`: a function f(x) -> Real. The slope fitting is then done over an indicator of the timeseries, which itself is estimated via a sliding window exactly as in [`SlidingWindowConfig`](@ref). When this is `nothing` the slope change is applied to the timeseries directly.
  * `width_ind, stride_ind, whichtime`: exactly as in [`SlidingWindowConfig`](@ref) if `indicator` is not `nothing`.
