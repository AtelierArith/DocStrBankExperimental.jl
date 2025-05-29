```julia
get_available_components(
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System;
    subsystem_name
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:PowerSystems.Component, I<:(Vector)}

```

Like [`get_components`](@ref) but returns only components that are [`get_available`](@ref).
