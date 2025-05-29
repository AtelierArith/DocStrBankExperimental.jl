```julia
integrate!(
    integral4items::AbstractArray{T},
    grid::ExtendableGrids.ExtendableGrid,
    AT::Type{<:ExtendableGrids.AssemblyType},
    integrand::GradientRobustMultiPhysics.AbstractUserDataType;
    index_offsets,
    time,
    items,
    force_quadrature_rule
)

```

各アイテムに結果を書き込む統合。
