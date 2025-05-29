```
IdealResidue{T<:AbstractFloat} <: AbstractMatrix{T}

IdealResidue{T}(backbone_geometry=DEFAULT_BACKBONE_GEOMETRY; template=nothing) where T
```

A 3x3 matrix representing the idealized geometry of a protein residue, with columns representing the N, Ca, and C atom positions of a residue positioned at the origin.
