```julia
get_time_series(
    ::Type{T<:InfrastructureSystems.TimeSeriesData},
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    name::AbstractString;
    start_time,
    len,
    count,
    resolution,
    features...
) -> Any

```

Return the exact stored data in a time series

This will load all forecast windows into memory by default. Be aware of how much data is stored.

Specify `start_time` and `len` if you only need a subset of data.

Does not apply a scaling factor multiplier.

# Arguments

  * `::Type{T}`: Concrete subtype of `TimeSeriesData` to return
  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `name::AbstractString`: name of time series
  * `resolution::Union{Nothing, Dates.Period} = nothing`: Required if resolution is needed  to uniquely identify the time series.
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: If nothing, use the `initial_timestamp` of the time series. If T is a subtype of Forecast then `start_time` must be the first timestamp of a window.
  * `len::Union{Nothing, Int} = nothing`: Length in the time dimension. If nothing, use the entire length.
  * `count::Union{Nothing, Int} = nothing`: Only applicable to subtypes of Forecast. Number of forecast windows starting at `start_time` to return. Defaults to all available.
  * `features...`: User-defined tags that differentiate multiple time series arrays for the same component attribute, such as different arrays for different scenarios or years

See also: [`get_time_series_array`](@ref), [`get_time_series_values`](@ref), [`get_time_series` by key](@ref get_time_series(     owner::TimeSeriesOwners,     key::TimeSeriesKey,     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     count::Union{Nothing, Int} = nothing, ))
