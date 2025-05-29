```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.Service,
    contributing_devices;
    kwargs...
)

```

Similar to [`add_component!`](@ref) but for services.

# Arguments

  * `sys::System`: system
  * `service::Service`: service to add
  * `contributing_devices`: Must be an iterable of type Device
