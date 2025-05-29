```julia
open_time_series_store!(
    func::Function,
    sys::PowerSystems.System;
    ...
) -> Any
open_time_series_store!(
    func::Function,
    sys::PowerSystems.System,
    mode,
    args...;
    kwargs...
) -> Any

```

Open the time series store for bulk additions or reads

This is recommended before calling `add_time_series!` many times because of the overhead associated with opening and closing an HDF5 file.

This is not necessary for an in-memory time series store.

# Examples

```julia
# Assume there is a system with an array of Components and SingleTimeSeries
# stored in the variables components and single_time_series, respectively
open_time_series_store!(sys, "r+") do
    for (component, ts) in zip(components, single_time_series)
        add_time_series!(sys, component, ts)
    end
end
```

You can also use this function to make reads faster. Change the mode from `"r+"` to `"r"` to open the file read-only.

See also: [`begin_time_series_update`](@ref)
