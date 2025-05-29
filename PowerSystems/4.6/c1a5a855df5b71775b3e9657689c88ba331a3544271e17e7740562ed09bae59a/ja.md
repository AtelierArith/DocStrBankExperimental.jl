```julia
get_components_by_name(
    _::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    name::AbstractString
) -> Vector{T} where T<:InfrastructureSystems.InfrastructureSystemsComponent

```

抽象型Tの名前を持つコンポーネントを取得します。PowerSystemsは各具体型に対して一意の名前を強制しますが、具体型間ではそうではありません。

具体型が知られている場合は、[`get_component`](@ref)を参照してください。

Tが抽象型でない場合はArgumentErrorをスローします。
