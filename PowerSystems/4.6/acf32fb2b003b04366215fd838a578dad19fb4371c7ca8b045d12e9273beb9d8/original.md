```julia
has_service(
    device::PowerSystems.Device,
    _::Type{T<:PowerSystems.Service}
) -> Bool

```

Return true if a service with type T is attached to the device.
