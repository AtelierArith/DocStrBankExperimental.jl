```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.ConstantReserveGroup,
    contributing_services::Vector{<:PowerSystems.Service};
    skip_validation,
    kwargs...
)

```

Similar to [`add_component!`](@ref) but for ConstantReserveGroup.

# Arguments

  * `sys::System`: system
  * `service::ConstantReserveGroup`: service to add
  * `contributing_services`: contributing services to the group
