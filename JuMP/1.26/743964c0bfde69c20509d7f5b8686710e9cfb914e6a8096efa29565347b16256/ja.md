```
add_bridge(
    model::GenericModel{T},
    BT::Type{<:MOI.Bridges.AbstractBridge};
    coefficient_type::Type{S} = T,
) where {T,S}
```

`BT{T}`を、サポートされていない制約を最適化ツールによってサポートされている制約のみを使用して同等の定式化に変換するために使用できるブリッジのリストに追加します。

関連情報: [`remove_bridge`](@ref).

## 例

```jldoctest
julia> model = Model();

julia> add_bridge(model, MOI.Bridges.Constraint.SOCtoNonConvexQuadBridge)

julia> add_bridge(
           model,
           MOI.Bridges.Constraint.NumberConversionBridge;
           coefficient_type = Complex{Float64}
       )
```
