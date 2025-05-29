```julia
agents_at(
    patch,
    model::EasyABM.SpaceModel2D
) -> Base.Generator{_A, F} where {_A, F<:(EasyABM.var"#169#170"{EasyABM.SpaceModel2D{T, S, P}} where {T, S<:Union{Float64, Int64}, P<:EasyABM.SType})}

```

指定されたパッチにいるエージェントのリストを返します。
