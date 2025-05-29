```julia
get_ndofs_all(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FEType::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> Int64

```

returns the total number of degrees of freedom for the given AssemblyType, FEType and geometry
