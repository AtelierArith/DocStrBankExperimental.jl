```julia
get_agents(
    model::EasyABM.SpaceModel3D{EasyABM.StaticType}
) -> Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.Agent3D{S, P, EasyABM.StaticType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType})

```
