```julia
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey
) -> Any
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey,
    start_time::Union{Nothing, Dates.DateTime}
) -> Any
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey,
    start_time::Union{Nothing, Dates.DateTime},
    len::Union{Nothing, Int64}
) -> Any
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey,
    start_time::Union{Nothing, Dates.DateTime},
    len::Union{Nothing, Int64},
    count::Union{Nothing, Int64}
) -> Any

```

Return the exact stored data in a time series, using a time series key look up

This will load all forecast windows into memory by default. Be aware of how much data is stored.

Specify start_time and len if you only need a subset of data.

Does not apply a scaling factor multiplier.

# Arguments

  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `key::TimeSeriesKey`: the time series' key
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: If nothing, use the `initial_timestamp` of the time series. If the time series is a subtype of Forecast then `start_time` must be the first timestamp of a window.
  * `len::Union{Nothing, Int} = nothing`: Length in the time dimension. If nothing, use the entire length.
  * `count::Union{Nothing, Int} = nothing`: Only applicable to subtypes of Forecast. Number of forecast windows starting at `start_time` to return. Defaults to all available.
  * `features...`: User-defined tags that differentiate multiple time series arrays for the same component attribute, such as different arrays for different scenarios or years

See also: [`get_time_series` by name](@ref get_time_series(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     count::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData})
