```
remove_bridge(
    model::GenericModel{S},
    BT::Type{<:MOI.Bridges.AbstractBridge};
    coefficient_type::Type{T} = S,
) where {S,T}

サポートされていない制約を最適化ツールによってサポートされている制約のみを使用して同等の定式化に変換するために使用できるブリッジのリストから `BT{T}` を削除します。

関連情報: [`add_bridge`](@ref).

## 例

```

jldoctest julia> model = Model();

julia> add_bridge(model, MOI.Bridges.Constraint.SOCtoNonConvexQuadBridge)

julia> remove_bridge(model, MOI.Bridges.Constraint.SOCtoNonConvexQuadBridge)

julia> add*bridge(            model,            MOI.Bridges.Constraint.NumberConversionBridge;            coefficient*type = Complex{Float64},        )

julia> remove*bridge(            model,            MOI.Bridges.Constraint.NumberConversionBridge;            coefficient*type = Complex{Float64},        ) ```
