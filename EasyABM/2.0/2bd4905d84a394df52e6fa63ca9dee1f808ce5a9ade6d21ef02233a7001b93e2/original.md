```julia
agents_at(
    patch,
    model::EasyABM.SpaceModel3D
) -> Base.Generator{_A, F} where {_A, F<:(EasyABM.var"#294#295"{EasyABM.SpaceModel3D{T, S, P}} where {T, S<:Union{Float64, Int64}, P<:EasyABM.SType})}

```

Returns list of agents at a given patch.
