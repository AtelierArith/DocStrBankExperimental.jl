```julia
get_component(
    _::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    name::AbstractString
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

型Tのコンポーネントを名前で取得します。一致するコンポーネントがない場合は何も返しません。Tが抽象型の場合、Tのすべてのサブタイプにわたるコンポーネントの名前は一意でなければなりません。

非一意の名前を持つ抽象型については、[`get_components_by_name`](@ref)を参照してください。

Tが具体型でなく、要求された名前のコンポーネントが複数ある場合はArgumentErrorをスローします。
