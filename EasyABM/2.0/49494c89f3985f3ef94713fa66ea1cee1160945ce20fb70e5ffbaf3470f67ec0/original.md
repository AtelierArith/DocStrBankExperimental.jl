```julia
get_agents(
    model::EasyABM.SpaceModel2D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType},
    condition::Function
) -> Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#172#174"{<:Function}), I<:(Base.Iterators.Flatten{I} where I<:(Base.Generator{UnitRange{Int64}, F} where F<:EasyABM.var"#171#173"))}

```
