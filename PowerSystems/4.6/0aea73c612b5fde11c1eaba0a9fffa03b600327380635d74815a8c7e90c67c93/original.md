```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.ConstantReserveGroup;
    skip_validation,
    kwargs...
)

```

Similar to [`add_component!`](@ref) but for ConstantReserveGroup.

# Arguments

  * `sys::System`: system
  * `service::ConstantReserveGroup`: service to add
