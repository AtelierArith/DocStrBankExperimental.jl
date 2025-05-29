```julia
get_available_components(
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System;
    subsystem_name
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:PowerSystems.Component, I<:(Vector)}

```

[`get_components`](@ref) と同様ですが、[`get_available`](@ref) のみを返すコンポーネントです。
