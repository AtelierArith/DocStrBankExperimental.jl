```julia
neighbors_moore(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType}
) -> Union{Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#282#283"{EasyABM.SpaceModel3D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.NPeriodicType}), Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#280#281"{EasyABM.SpaceModel3D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.PeriodicType})}
neighbors_moore(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType},
    dist::Int64
) -> Union{Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#282#283"{EasyABM.SpaceModel3D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.NPeriodicType}), Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#280#281"{EasyABM.SpaceModel3D{EasyABM.StaticType, S, P}} where {S<:Union{Float64, Int64}, P<:EasyABM.PeriodicType})}

```
