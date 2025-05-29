```julia
add_time_series!(
    sys::PowerSystems.System,
    file_metadata::Vector{InfrastructureSystems.TimeSeriesFileMetadata};
    resolution
) -> Vector{InfrastructureSystems.TimeSeriesKey}

```

Add time series data from a metadata file or metadata descriptors.

# Arguments

  * `sys::System`: system
  * `timeseries_metadata::Vector{IS.TimeSeriesFileMetadata}`: metadata for timeseries
  * `resolution::DateTime.Period=nothing`: skip time series that don't match this resolution.
