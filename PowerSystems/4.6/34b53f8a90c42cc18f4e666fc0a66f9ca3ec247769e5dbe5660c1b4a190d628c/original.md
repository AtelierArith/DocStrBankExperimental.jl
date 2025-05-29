```julia
get_component(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

Get the component of the [`System`](@ref) that makes up the [`SingularComponentSelector`](@ref); `nothing` if there is none. Optionally specify a filter function `scope_limiter` as the first argument to limit the components that should be considered.

# Arguments

  * `scope_limiter::Union{Function, Nothing}`: see [`ComponentSelector`](@ref)
  * `selector::SingularComponentSelector`: the `SingularComponentSelector` whose component to retrieve
  * `sys::System`: the system from which to draw components
