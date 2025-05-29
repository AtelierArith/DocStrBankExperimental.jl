```julia
Dofmap4AssemblyType(
    FES::ExtendableFEMBase.FESpace,
    AT::Type{<:ExtendableGrids.AssemblyType}
) -> Any

```

yields the coressponding dofmap of the FESpace for a given AssemblyType (assumed with respect to the (parent)grid of the FESpace)
