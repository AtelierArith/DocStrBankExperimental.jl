```julia
abstract type ReconstructionNormalFlux{FEreconst<:GradientRobustMultiPhysics.AbstractFiniteElement} <: ??
```

reconstruction normal flux: evaluates the normal flux of a reconstructed version of the finite element function.

FEreconst specifies the reconstruction space and reconstruction algorithm if it is defined for the finite element that it is applied to.
