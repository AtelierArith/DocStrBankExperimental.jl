```julia
get_basis(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FEType::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableFEMBase.var"#closure#123"

```

returns the closure function of form

```
closure(refbasis, xref)
```

that computes the evaluations of the basis functions on the reference geometry
