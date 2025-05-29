```julia
get_groups(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

Get the groups that make up the [`ComponentSelector`](@ref).

# Arguments

  * `selector::ComponentSelector`: the `ComponentSelector` whose groups to retrieve
  * `sys::System`: the system from which to draw components
