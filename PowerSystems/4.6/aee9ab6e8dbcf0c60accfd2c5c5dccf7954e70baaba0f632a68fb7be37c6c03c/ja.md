```julia
get_available_component(
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    args...;
    kwargs...
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

[`get_component`](@ref)と同様ですが、コンポーネントが[`get_available`](@ref)でない場合は`nothing`も返します。
