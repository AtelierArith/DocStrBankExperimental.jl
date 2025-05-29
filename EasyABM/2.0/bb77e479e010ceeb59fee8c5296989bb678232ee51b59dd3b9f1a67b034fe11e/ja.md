```julia
neighbors_moore(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Union{Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#157#158"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.NPeriodicType}), Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#155#156"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.PeriodicType})}
neighbors_moore(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType, S<:Union{Float64, Int64}, P<:EasyABM.SType},
    dist::Int64
) -> Union{Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#157#158"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.NPeriodicType}), Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#155#156"{EasyABM.SpaceModel2D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.PeriodicType})}

```
