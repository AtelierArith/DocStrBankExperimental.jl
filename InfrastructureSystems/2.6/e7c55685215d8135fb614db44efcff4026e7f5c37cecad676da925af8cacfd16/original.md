```julia
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries;
    ...
) -> Vector{D} where D<:Dates.TimeType
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries,
    start_time::Union{Nothing, Dates.DateTime};
    len
) -> Vector{D} where D<:Dates.TimeType

```

Return a vector of timestamps from a cached StaticTimeSeries instance.

# Arguments

  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `time_series::StaticTimeSeries`: subtype of `StaticTimeSeries` (e.g., `SingleTimeSeries`)
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: the first timestamp to retrieve. If nothing, use the `initial_timestamp` of the time series.
  * `len::Union{Nothing, Int} = nothing`: Length of time-series to retrieve (i.e. number of timestamps). If nothing, use the entire length

See also: [`get_time_series_array`](@ref get_time_series_array(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`get_time_series_values`](@ref get_time_series_values(owner::TimeSeriesOwners, time_series::StaticTimeSeries, start_time::Union{Nothing, Dates.DateTime} = nothing; len::Union{Nothing, Int} = nothing, ignore_scaling_factors = false)), [`StaticTimeSeriesCache`](@ref), [`get_time_series_timestamps` by name from storage](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_timestamps` from a `ForecastCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, ))
