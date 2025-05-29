```julia
add_time_series!(
    sys::PowerSystems.System,
    metadata_file::AbstractString;
    resolution
) -> Vector{InfrastructureSystems.TimeSeriesKey}

```

Add time series data from a metadata file or metadata descriptors.

# Arguments

  * `sys::System`: system
  * `metadata_file::AbstractString`: metadata file for timeseries that includes an array of IS.TimeSeriesFileMetadata instances or a vector.
  * `resolution::DateTime.Period=nothing`: skip time series that don't match this resolution.
