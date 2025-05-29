```julia
get_agents(
    model::EasyABM.SpaceModel2D{EasyABM.StaticType}
) -> Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.Agent2D{S, P, EasyABM.StaticType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType})

```
