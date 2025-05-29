```julia
get_existing_device_types(
    sys::PowerSystems.System
) -> Vector{DataType}

```

Return all the device types in the system. It does not return component types or masked components.
