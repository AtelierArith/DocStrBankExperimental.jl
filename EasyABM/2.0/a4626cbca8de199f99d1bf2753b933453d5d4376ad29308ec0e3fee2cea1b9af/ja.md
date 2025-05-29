```julia
neighbors_neumann(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType}
) -> Union{Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#161#162"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.NPeriodicType}), Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#159#160"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.PeriodicType})}
neighbors_neumann(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType},
    dist::Int64
) -> Union{Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#161#162"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.NPeriodicType}), Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#159#160"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.PeriodicType})}

```
