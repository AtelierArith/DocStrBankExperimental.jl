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

Integration that writes result on every item into integral4items.
