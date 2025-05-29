```julia
get_agents(
    model::EasyABM.SpaceModel2D{EasyABM.StaticType},
    condition::Function
) -> Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#179#180"{<:Function}), I<:(Array{EasyABM.Agent2D{S, P, EasyABM.StaticType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType})}

```
