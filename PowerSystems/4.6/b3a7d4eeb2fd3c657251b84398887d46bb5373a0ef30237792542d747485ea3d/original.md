```julia
get_components(
    filter_func::Function,
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System;
    subsystem_name
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:PowerSystems.Component, I<:(Vector)}

```

Return an iterator of components of a given `Type` from a [`System`](@ref), using an additional filter

`T` can be a concrete or abstract [`Component`](@ref) type from the [Type Tree](@ref). Call collect on the result if an array is desired.

# Examples

```julia
iter_coal = get_components(x -> get_fuel(x) == ThermalFuels.COAL, Generator, sys)
pv_gens =
    collect(get_components(x -> get_prime_mover_type(x) == PrimeMovers.PVe, Generator, sys))
```

See also: [`get_components`](@ref get_components(     ::Type{T},     sys::System;     subsystem_name = nothing, ) where {T <: Component}), [`get_available_components`](@ref), [`get_buses`](@ref)
