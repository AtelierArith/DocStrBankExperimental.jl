```julia
get_basissubset(
    ::Type{<:ExtendableGrids.AssemblyType},
    FE::ExtendableFEMBase.FESpace{Tv, Ti, FEType<:ExtendableFEMBase.AbstractFiniteElement, APT},
    ::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableFEMBase.var"#closure#268"{_A, Int64} where _A
get_basissubset(
    ::Type{<:ExtendableGrids.AssemblyType},
    FE::ExtendableFEMBase.FESpace{Tv, Ti, FEType<:ExtendableFEMBase.AbstractFiniteElement, APT},
    ::Type{<:ExtendableGrids.AbstractElementGeometry},
    xgrid
) -> Union{ExtendableFEMBase.var"#21#22", ExtendableFEMBase.var"#closure#277"{_A, _B, _C, Int64, Int64} where {_A, _B, _C}}

```

returns a closure function of the form

```
closure(subset_ids::Array{Int, 1}, cell)
```

which returns the ids of the local basis functions needed on the cell. Usually, subset_ids = 1:ndofs (meaning that all basis functions on the reference cells are used),

See e.g. the 3D implementation of BDM1 or H1P3 where different basis functions are chosen depending on the face orientations (which in 3D is not just a sign)
