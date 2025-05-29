```julia
get_time_series_timestamps(
    ::Type{T<:InfrastructureSystems.TimeSeriesData},
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    name::AbstractString;
    resolution,
    start_time,
    len,
    features...
) -> Vector{D} where D<:Dates.TimeType

```

Return a vector of timestamps from storage for the given time series parameters.

# Arguments

  * `::Type{T}`: the type of time series (a concrete subtype of `TimeSeriesData`)
  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `name::AbstractString`: name of time series
  * `resolution::Union{Nothing, Dates.Period} = nothing`: Required if resolution is needed  to uniquely identify the time series.
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: If nothing, use the `initial_timestamp` of the time series. If T is a subtype of [`Forecast`](@ref) then `start_time` must be the first timestamp of a window.
  * `len::Union{Nothing, Int} = nothing`: Length of time-series to retrieve (i.e. number of timestamps). If nothing, use the entire length.
  * `features...`: User-defined tags that differentiate multiple time series arrays for the same component attribute, such as different arrays for different scenarios or years

See also: [`get_time_series_array`](@ref get_time_series_array(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_values`](@ref get_time_series_values(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, features...,) where {T <: TimeSeriesData}), [`get_time_series_timestamps` from a `StaticTimeSeriesCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, )), [`get_time_series_timestamps` from a `ForecastCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, ))
