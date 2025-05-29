```
struct PatchDecomposition{Dr,Dc,Dp} <: DiscreteModel{Dc,Dp}
```

Represents a patch decomposition of a discrete model, i.e an overlapping cell covering `{Ω_i}` of `Ω` such that `Ω = Σ_i Ω_i`.

## Properties:

  * `Dr::Integer` : Dimension of the patch root
  * `model::DiscreteModel{Dc,Dp}` : Underlying discrete model
  * `patch_cells::Table` : [patch][local cell] -> cell
  * `patch_cells_faces_on_boundary::Table` : [d][overlapped cell][local face] -> face is on patch boundary
