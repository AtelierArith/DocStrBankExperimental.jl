```julia
agent_with_id(
    i::Int64,
    model::EasyABM.GraphModel{T<:EasyABM.MType, EasyABM.StaticType}
) -> Union{Nothing, EasyABM.GraphAgent{S, EasyABM.StaticType} where S<:EasyABM.MType}

```

Returns agent having given id.
