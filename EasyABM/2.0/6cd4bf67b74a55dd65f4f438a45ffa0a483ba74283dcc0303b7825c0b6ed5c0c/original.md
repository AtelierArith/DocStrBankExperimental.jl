```julia
neighbors(
    agent::EasyABM.GraphAgent,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.StaticType}}
) -> Base.Iterators.Flatten{I} where I<:(Base.Generator{UnitRange{Int64}, F} where F<:EasyABM.var"#520#521")

```

Returns agents on neighboring nodes of given agent.
