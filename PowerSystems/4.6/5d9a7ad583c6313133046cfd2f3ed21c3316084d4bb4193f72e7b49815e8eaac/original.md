```julia
get_component(
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

Get the component of the [`System`](@ref) that makes up the [`SingularComponentSelector`](@ref); `nothing` if there is none.

# Arguments

  * `selector::SingularComponentSelector`: the `SingularComponentSelector` whose component to retrieve
  * `sys::System`: the system from which to draw components
