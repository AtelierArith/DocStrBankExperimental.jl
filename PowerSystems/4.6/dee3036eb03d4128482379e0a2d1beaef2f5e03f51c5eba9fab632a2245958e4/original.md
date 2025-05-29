```julia
add_service!(
    device::PowerSystems.Device,
    service::PowerSystems.Service,
    sys::PowerSystems.System
)

```

Similar to [`add_service!`](@ref) but for Service and Device already stored in the system. Performs validation checks on the device and the system

# Arguments

  * `device::Device`: Device
  * `service::Service`: Service
  * `sys::System`: system
