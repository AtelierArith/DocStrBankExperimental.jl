```julia
abstract type AbstractLorentzVector{T} <: StaticArraysCore.FieldVector{4, T}
```

Abstract type to model generic Lorentz vectors, i.e. elements of a minkowski-like space, where the component space is arbitray.
