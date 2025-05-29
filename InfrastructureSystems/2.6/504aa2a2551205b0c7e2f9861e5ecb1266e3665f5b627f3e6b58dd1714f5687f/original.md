```julia
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    forecast::InfrastructureSystems.Forecast;
    ...
)
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    forecast::InfrastructureSystems.Forecast,
    start_time::Union{Nothing, Dates.DateTime};
    len
) -> Vector{D} where D<:Dates.TimeType

```

Return a vector of timestamps from a cached Forecast instance.

# Arguments

  * `owner::TimeSeriesOwners`: Component or attribute containing the time series
  * `forecast::Forecast`: a concrete subtype of [`Forecast`](@ref)
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: the first timestamp of one of the forecast windows
  * `len::Union{Nothing, Int} = nothing`: Length of time-series to retrieve (i.e. number of timestamps). If nothing, use the entire length.

See also: [`get_time_series_array`](@ref get_time_series_array(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len = nothing,     ignore_scaling_factors = false, )), [`get_time_series_values`](@ref get_time_series_values(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`ForecastCache`](@ref), [`get_time_series_timestamps` by name from storage](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_timestamps` from a `StaticTimeSeriesCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, ))
