```julia
get_components(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

Get the components of the [`System`](@ref) that make up the [`ComponentSelector`](@ref). Optionally specify a filter function `scope_limiter` as the first argument to limit the components that should be considered.

# Arguments

  * `scope_limiter::Union{Function, Nothing}`: see [`ComponentSelector`](@ref)
  * `selector::ComponentSelector`: the `ComponentSelector` whose components to retrieve
  * `sys::System`: the system from which to draw components
