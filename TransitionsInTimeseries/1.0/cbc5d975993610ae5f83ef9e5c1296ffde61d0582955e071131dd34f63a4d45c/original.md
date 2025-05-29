```
ChangesConfig
```

Supertype for how "changes" in a timeseries are estimated in [`estimate_changes`](@ref). "Changes" deemed statistically significant in [`significant_transitions`](@ref) are "transitions" in the timeseries.

Existing subtypes of `ChangesConfig` are:

  * [`SlidingWindowConfig`](@ref).
  * [`SegmentedWindowConfig`](@ref).
  * [`SlopeChangeConfig`](@ref).
