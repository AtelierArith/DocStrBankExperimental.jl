```
transferfield!(
    ff::F,
    fensf::FENodeSet{FT},
    fesf::AbstractFESet,
    fc::F,
    fensc::FENodeSet{FT},
    fesc::AbstractFESet,
    geometricaltolerance::FT;
    parametrictolerance::FT = 0.01,
) where {FT<:Number, F<:ElementalField{T}, T}
```

Transfer an elemental field from a coarse mesh to a finer one.

# Arguments

  * `ff` = the fine-mesh field (modified and also returned)
  * `fensf` = finite element node set for the fine-mesh
  * `fc` = the coarse-mesh field
  * `fensc` = finite element node set for the fine-mesh,
  * `fesc` = finite element set for the coarse mesh
  * `tolerance` = tolerance in physical space for searches of the adjacent nodes

# Output

Elemental field `ff` transferred to the fine mesh is output.
