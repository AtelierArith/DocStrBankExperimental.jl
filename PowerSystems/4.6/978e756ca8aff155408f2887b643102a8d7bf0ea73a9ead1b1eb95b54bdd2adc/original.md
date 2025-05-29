```julia
transform_single_time_series!(
    sys::PowerSystems.System,
    horizon::Dates.Period,
    interval::Dates.Period;
    resolution
)

```

Transform all instances of [`SingleTimeSeries`](@ref) in a `System` to [`DeterministicSingleTimeSeries`](@ref)

This can be used to generate a perfect forecast from historical measurements or realizations when actual forecasts are unavailable, without unnecessarily duplicating data.

If all `SingleTimeSeries` instances cannot be transformed then none will be.

Any existing `DeterministicSingleTimeSeries` forecasts will be deleted even if the inputs are invalid.

# Arguments

  * `sys::System`: System containing the components.
  * `horizon::Dates.Period`: desired [horizon](@ref H) of each forecast [window](@ref W)
  * `interval::Dates.Period`: desired [interval](@ref I) between forecast [windows](@ref W)
  * `resolution::Union{Nothing, Dates.Period} = nothing`: If set, only transform time series  with this resolution.
