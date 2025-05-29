```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.Service,
    contributing_device::PowerSystems.Device;
    kwargs...
)

```

Similar to [`add_component!`](@ref) but for services.

# Arguments

  * `sys::System`: system
  * `service::Service`: service to add
  * `contributing_device::Device`: Valid Device
