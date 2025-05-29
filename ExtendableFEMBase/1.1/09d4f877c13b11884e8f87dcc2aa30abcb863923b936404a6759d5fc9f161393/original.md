```julia
get_ndofs(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FEType::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> Any

```

returns the number of degrees of freedom for the given AssemblyType, FEType and geometry
