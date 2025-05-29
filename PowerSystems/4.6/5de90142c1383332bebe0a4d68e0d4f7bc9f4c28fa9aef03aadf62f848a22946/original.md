```julia
System(
    data::PowerSystems.PowerSystemTableData;
    time_series_resolution,
    time_series_in_memory,
    time_series_directory,
    runchecks,
    kwargs...
) -> PowerSystems.System

```

Construct a System from PowerSystemTableData data.

# Arguments

  * `time_series_resolution::Union{DateTime, Nothing}=nothing`: only store time_series that match this resolution.
  * `time_series_in_memory::Bool=false`: Store time series data in memory instead of HDF5 file
  * `time_series_directory=nothing`: Store time series data in directory instead of tmpfs
  * `runchecks::Bool=true`: Validate struct fields.

Throws DataFormatError if time_series with multiple resolutions are detected.

  * A time_series has a different resolution than others.
  * A time_series has a different horizon than others.
