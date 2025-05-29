```julia
integrate(
    grid::ExtendableGrids.ExtendableGrid,
    AT::Type{<:ExtendableGrids.AssemblyType},
    integrand!::GradientRobustMultiPhysics.AbstractUserDataType,
    resultdim::Int64;
    T,
    items,
    force_quadrature_rule
) -> Union{Float64, Vector{Float64}}

```

Integration that returns total integral.
