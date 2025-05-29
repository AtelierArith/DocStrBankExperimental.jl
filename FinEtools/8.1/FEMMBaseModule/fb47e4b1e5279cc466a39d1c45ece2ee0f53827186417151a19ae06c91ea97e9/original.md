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
) where {FT<:Number, F<:NodalField{T}, T}
```

Transfer a nodal field from a coarse mesh to a finer one.

# Arguments

  * `ff` = the fine-mesh field (modified and also returned)
  * `fensf` = finite element node set for the fine-mesh
  * `fc` = the coarse-mesh field
  * `fensc` = finite element node set for the fine-mesh,
  * `fesc` = finite element set for the coarse mesh
  * `geometricaltolerance` = tolerance in physical space for searches of the adjacent nodes
  * `parametrictolerance` = tolerance in parametric space for for check whether node is inside an element

# Output

Nodal field `ff` transferred to the fine mesh is output.
