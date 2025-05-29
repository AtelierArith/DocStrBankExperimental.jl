```julia
get_agents(
    model::EasyABM.GraphModel{T<:EasyABM.MType, EasyABM.StaticType}
) -> Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.GraphAgent{T, EasyABM.StaticType}, 1} where T<:EasyABM.MType)

```
