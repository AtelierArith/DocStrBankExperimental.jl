```julia
get_forecast_initial_times(
    sys::PowerSystems.System
) -> Union{Vector{Any}, Vector{Dates.DateTime}, StepRangeLen{T, R, S, Int64} where {T, R>:Dates.DateTime, S}}

```

Return the initial times for all forecasts.
