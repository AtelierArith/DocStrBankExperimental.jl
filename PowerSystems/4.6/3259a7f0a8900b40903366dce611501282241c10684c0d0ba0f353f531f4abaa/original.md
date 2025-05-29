A power system

`System` is the main data container in PowerSystems.jl, including basic metadata (base power, frequency), components (network topology, loads, generators, and services), and time series data.

```julia
System(base_power)
System(base_power, buses, components...)
System(base_power, buses, generators, loads, branches, storage, services; kwargs...)
System(base_power, buses, generators, loads; kwargs...)
System(file; kwargs...)
System(; buses, generators, loads, branches, storage, base_power, services, kwargs...)
System(; kwargs...)
```

# Arguments

  * `base_power::Float64`: the base power value for the system
  * `buses::Vector{ACBus}`: an array of buses
  * `components...`: Each element (e.g., `buses`, `generators`, ...) must be an iterable   containing subtypes of `Component`.

# Keyword arguments

  * `ext::Dict`: Contains user-defined parameters. Should only contain standard types.
  * `frequency::Float64`: (default = 60.0) Operating frequency (Hz)
  * `runchecks::Bool`: Run available checks on input fields and when add_component! is called. Throws InvalidValue if an error is found.
  * `time_series_in_memory::Bool=false`: Store time series data in memory instead of HDF5.
  * `time_series_directory::Union{Nothing, String}`: Directory for the time series HDF5 file.   Defaults to the tmp file system
  * `enable_compression::Bool=false`: Enable compression of time series data in HDF5.
  * `compression::CompressionSettings`: Allows customization of HDF5 compression settings.
  * `config_path::String`: specify path to validation config file
  * `unit_system::String`: (Default = `"SYSTEM_BASE"`) Set the unit system for   [per-unitization](@ref per_unit) while getting and setting data (`"SYSTEM_BASE"`,       `"DEVICE_BASE"`, or `"NATURAL_UNITS"`)

By default, time series data is stored in an HDF5 file in the tmp file system to prevent large datasets from overwhelming system memory (see [Data Storage](@ref)). **If the system's time series data will be larger than the amount of tmp space available**, use the `time_series_directory` parameter to change its location. You can also override the location by setting the environment variable `SIENNA_TIME_SERIES_DIRECTORY` to another directory.

HDF5 compression is not enabled by default, but you can enable it with `enable_compression` to get significant storage savings at the cost of CPU time. [`CompressionSettings`](@ref) can be used to customize the HDF5 compression.

If you know that your dataset will fit in your computer's memory, then you can increase performance by storing it in memory with `time_series_in_memory`.

# Examples

```julia
sys = System(100.0; enable_compression = true)
sys = System(100.0; compression = CompressionSettings(
    enabled = true,
    type = CompressionTypes.DEFLATE,  # BLOSC is also supported
    level = 3,
    shuffle = true)
)
sys = System(100.0; time_series_in_memory = true)
```
