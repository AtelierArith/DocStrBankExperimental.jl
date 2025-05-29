```
mutable struct DensityMatrixMixtureParameters <: NoiseParameters
```

The `DensityMatrixMixtureParameters` struct represents the parameters for a density matrix mixture noise model. It is a mutable struct that holds two density matrices, ρ₁ and ρ₂.

# Fields

  * `ρ₁::Union{DensityMatrix,Qureg}`: The first density matrix.
  * `ρ₂::Union{DensityMatrix,Qureg}`: The second density matrix.
