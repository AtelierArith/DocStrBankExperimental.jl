```julia
agent_with_id(
    i::Int64,
    model::EasyABM.GraphModel{T<:EasyABM.MType, EasyABM.MortalType}
) -> Union{Nothing, EasyABM.GraphAgent{T, EasyABM.MortalType} where T<:EasyABM.MType}

```

Returns agent having given id.
