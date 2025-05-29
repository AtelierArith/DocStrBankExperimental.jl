```
AbstractTissueProperties{N,T} <: FieldVector{N,T}
```

Abstract type for custom structs that hold tissue properties used for a simulation within one voxel. For simulations, `SimulationParameters`s are used that can be assembled with the `@parameters` macro.

# Possible fields:

  * `T₁::T`: T₁ relaxation parameters of a voxel
  * `T₂::T`: T₂ relaxation parameters of a voxel
  * `B₁::T`: Scaling factor for effective B₁ excitation field within a voxel
  * `B₀::T`: Off-resonance with respect to main magnetic field within a voxel
  * `ρˣ::T`: Real part of proton density within a voxel
  * `ρʸ::T`: Imaginary part of proton density within a voxel

# Implementation details:

The structs are subtypes of FieldVector, which is a StaticVector with named fields (see the documentation of StaticArrays.jl). There are three reasons for letting the structs be subtypes of FieldVector:

1. FieldVectors/StaticVectors have sizes that are known at compile time. This is beneficial for performance reasons
2. The named fields improve readability of the code (e.g. `p.B₁` vs `p[3]`)
3. Linear algebra operations can be performed on instances of the structs. This allows, for example, subtraction (without having to manually define methods) and that is useful for comparing parameter maps.
