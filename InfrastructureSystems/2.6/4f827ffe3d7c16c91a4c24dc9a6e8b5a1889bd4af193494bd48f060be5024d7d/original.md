```julia
get_time_series_values(
    ::Type{T<:InfrastructureSystems.TimeSeriesData},
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    name::AbstractString;
    resolution,
    start_time,
    len,
    ignore_scaling_factors,
    features...
) -> Any

```

Return an vector of timeseries data without timestamps from storage

If the data size is small and this will be called many times, consider using the version that accepts a cached `TimeSeriesData` instance.

# Arguments

  * `::Type{T}`: type of the time series (a concrete subtype of `TimeSeriesData`)
  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `name::AbstractString`: name of time series
  * `resolution::Union{Nothing, Dates.Period} = nothing`: Required if resolution is needed  to uniquely identify the time series.
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: If nothing, use the `initial_timestamp` of the time series. If T is a subtype of [`Forecast`](@ref) then `start_time` must be the first timestamp of a window.
  * `len::Union{Nothing, Int} = nothing`: Length of time-series to retrieve (i.e. number of timestamps). If nothing, use the entire length.
  * `ignore_scaling_factors = false`: If `true`, the time-series data will be multiplied by the result of calling the stored `scaling_factor_multiplier` function on the `owner`
  * `features...`: User-defined tags that differentiate multiple time series arrays for the same component attribute, such as different arrays for different scenarios or years

See also: [`get_time_series_array`](@ref get_time_series_array(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_timestamps`](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series`](@ref), [`get_time_series_values` from a `StaticTimeSeriesCache`](@ref get_time_series_values(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`get_time_series_values` from a `ForecastCache`](@ref get_time_series_values(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, ))
