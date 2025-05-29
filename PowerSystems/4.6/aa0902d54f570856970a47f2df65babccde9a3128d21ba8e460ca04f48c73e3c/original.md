```julia
remove_time_series!(
    sys::PowerSystems.System,
    _::Type{T<:InfrastructureSystems.TimeSeriesData}
)

```

Remove all the time series data for a time series type.

See also: [`clear_time_series!`](@ref)

If you are storing time series data in an HDF5 file, `remove_time_series!` does not actually free up file space (HDF5 behavior). If you want to remove all or most time series instances then consider using `clear_time_series!`. It will delete the HDF5 file and create a new one. PowerSystems has plans to automate this type of workflow.
