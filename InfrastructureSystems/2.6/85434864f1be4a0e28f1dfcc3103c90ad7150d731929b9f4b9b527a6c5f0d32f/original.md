Construct StaticTimeSeriesCache to automatically control caching of time series data. Maintains rows of data in memory based on `cache_size_bytes`.

Call Base.iterate or [`get_time_series_array`](@ref) to retrieve data. Each iteration will return a TimeSeries.TimeArray of size 1.

# Arguments

  * `::Type{T}`: subtype of StaticTimeSeries
  * `component::InfrastructureSystemsComponent`: component
  * `name::AbstractString`: time series name
  * `cache_size_bytes = TIME_SERIES_CACHE_SIZE_BYTES`: maximum size of data to keep in memory
  * `ignore_scaling_factors = false`: controls whether to ignore `scaling_factor_multiplier` in the time series instance
