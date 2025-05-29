```julia
out_neighbors(
    agent::EasyABM.GraphAgent,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}}
) -> Union{Base.Generator{UnitRange{Int64}, typeof(identity)}, Base.Iterators.Flatten{I} where I<:(Base.Generator{UnitRange{Int64}, F} where F<:EasyABM.var"#522#523")}

```

Returns agents on neighboring outgoing nodes of given agent.
