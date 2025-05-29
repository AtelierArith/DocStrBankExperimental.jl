```julia
agent_with_id(
    i::Int64,
    model::EasyABM.GraphModel{T<:EasyABM.MType, EasyABM.StaticType}
) -> Union{Nothing, EasyABM.GraphAgent{T, EasyABM.StaticType} where T<:EasyABM.MType}

```

Returns agent having given id.
