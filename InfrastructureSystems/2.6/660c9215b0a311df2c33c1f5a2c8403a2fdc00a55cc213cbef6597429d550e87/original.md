```julia
get_time_series_values(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries;
    ...
) -> Any
get_time_series_values(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries,
    start_time::Union{Nothing, Dates.DateTime};
    len,
    ignore_scaling_factors
) -> Any

```

Return an vector of timeseries data without timestamps from a cached `StaticTimeSeries` instance

# Arguments

  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `time_series::StaticTimeSeries`: subtype of `StaticTimeSeries` (e.g., `SingleTimeSeries`)
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: the first timestamp to retrieve. If nothing, use the `initial_timestamp` of the time series.
  * `len::Union{Nothing, Int} = nothing`: Length of time-series to retrieve (i.e. number of timestamps). If nothing, use the entire length
  * `ignore_scaling_factors = false`: If `true`, the time-series data will be multiplied by the result of calling the stored `scaling_factor_multiplier` function on the `owner`

See also: [`get_time_series_array`](@ref get_time_series_array(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`get_time_series_timestamps`](@ref get_time_series_timestamps(owner::TimeSeriesOwners, time_series::StaticTimeSeries, start_time::Union{Nothing, Dates.DateTime} = nothing; len::Union{Nothing, Int} = nothing,)), [`StaticTimeSeriesCache`](@ref), [`get_time_series_values` by name from storage](@ref get_time_series_values(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_values` from a `ForecastCache`](@ref get_time_series_values(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, ))
