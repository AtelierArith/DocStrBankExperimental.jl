```julia
get_available_component(
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    args...;
    kwargs...
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

Like [`get_component`](@ref) but also returns `nothing` if the component is not [`get_available`](@ref).
