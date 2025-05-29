```julia
get_agents(
    model::EasyABM.SpaceModel3D{EasyABM.StaticType},
    condition::Function
) -> Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#304#305"{<:Function}), I<:(Array{EasyABM.Agent3D{S, P, EasyABM.StaticType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType})}

```
