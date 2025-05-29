```julia
in_neighbors(
    agent::EasyABM.GraphAgent,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}}
) -> Union{Base.Generator{UnitRange{Int64}, typeof(identity)}, Base.Iterators.Flatten{I} where I<:(Base.Generator{UnitRange{Int64}, F} where F<:EasyABM.var"#526#527")}

```

Returns agents on neighboring incoming nodes of given agent.
