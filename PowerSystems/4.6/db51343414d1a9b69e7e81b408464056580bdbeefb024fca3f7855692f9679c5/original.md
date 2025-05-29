```julia
get_time_limits(
    value::PowerSystems.HydroDispatch
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

Get [`HydroDispatch`](@ref) `time_limits`.
