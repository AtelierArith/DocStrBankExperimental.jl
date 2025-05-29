```julia
clear_time_series!(sys::PowerSystems.System)

```

Clear all time series data from the system.

If you are storing time series data in an HDF5 file, this will will delete the HDF5 file and create a new one.

See also: [`remove_time_series!`](@ref remove_time_series!(sys::System, ::Type{T}) where {T <: TimeSeriesData})
