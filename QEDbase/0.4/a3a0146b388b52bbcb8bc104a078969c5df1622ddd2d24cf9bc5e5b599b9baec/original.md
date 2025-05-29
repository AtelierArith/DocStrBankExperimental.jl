```julia
abstract type AbstractDiracMatrix{T} <: StaticArraysCore.FieldMatrix{4, 4, T}
```

Abstract type for Dirac matrices, i.e. matrix representations for linear mappings from a spinor space into another.
