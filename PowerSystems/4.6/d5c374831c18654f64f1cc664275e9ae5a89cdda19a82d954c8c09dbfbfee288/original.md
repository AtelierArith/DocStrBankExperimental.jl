```julia
get_components(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

Get the components of the [`System`](@ref) that make up the [`ComponentSelector`](@ref).

# Arguments

  * `selector::ComponentSelector`: the `ComponentSelector` whose components to retrieve
  * `sys::System`: the system from which to draw components
