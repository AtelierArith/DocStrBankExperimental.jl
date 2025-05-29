Construct ForecastCache to automatically control caching of forecast data. Maintains some count of forecast windows in memory based on `cache_size_bytes`.

Call Base.iterate or [`get_next_time_series_array!`](@ref) to retrieve data. Each iteration will return a TimeSeries.TimeArray covering one forecast window of length `horizon_count`.

# Arguments

  * `::Type{T}`: subtype of Forecast
  * `component::InfrastructureSystemsComponent`: component
  * `name::AbstractString`: forecast name
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: forecast start time
  * `horizon_count::Union{Nothing, Int} = nothing`: forecast horizon count
  * `cache_size_bytes = TIME_SERIES_CACHE_SIZE_BYTES`: maximum size of data to keep in memory
  * `ignore_scaling_factors = false`: controls whether to ignore `scaling_factor_multiplier` in the time series instance
