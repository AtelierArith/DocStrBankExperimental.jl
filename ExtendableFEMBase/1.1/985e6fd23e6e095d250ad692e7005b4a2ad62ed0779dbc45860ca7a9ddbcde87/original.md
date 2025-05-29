```julia
get_polynomialorder(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FE::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> Int64

```

returns the expected polynomial order of the basis functions (used to determine default quadrature orders)
