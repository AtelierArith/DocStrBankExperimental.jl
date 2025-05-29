```julia
get_components(
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System;
    subsystem_name
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:PowerSystems.Component, I<:(Vector)}

```

Return an iterator of components of a given `Type` from a [`System`](@ref).

`T` can be a concrete or abstract [`Component`](@ref) type from the [Type Tree](@ref). Call collect on the result if an array is desired.

# Examples

```julia
iter = get_components(ThermalStandard, sys)
iter = get_components(Generator, sys)
generators = collect(get_components(Generator, sys))
```

See also: [`iterate_components`](@ref), [`get_components` with a filter](@ref get_components(     filter_func::Function,     ::Type{T},     sys::System;     subsystem_name = nothing, ) where {T <: Component}), [`get_available_components`](@ref), [`get_buses`](@ref)
