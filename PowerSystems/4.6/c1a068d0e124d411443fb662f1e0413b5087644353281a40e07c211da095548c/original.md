```julia
remove_service!(
    device::PowerSystems.Device,
    service::PowerSystems.Service
)

```

Remove a service from a device.

Throws ArgumentError if the service is not attached to the device.
