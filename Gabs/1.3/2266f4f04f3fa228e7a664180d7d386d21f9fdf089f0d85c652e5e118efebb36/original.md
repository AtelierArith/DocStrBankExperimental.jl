```
attenuator([Td=Vector{Float64}, Tt=Matrix{Float64},] basis::SymplecticBasis, theta<:Real, n<:Int)
```

Gaussian channel describing the coupling of an input single mode Gaussian state and its environment via a beam splitter operation. The channel is paramatrized by beam splitter rotation angle `theta` and thermal noise `n`.

## Mathematical description of an attenuator channel

An attenuator channel, `E(θ, nₜₕ)`, where `θ` is the beam splitter rotation parameter and `nₜₕ ≥ 1` is the thermal noise parameter, is characterized by the zero displacement vector, transformation matrix `cos(θ)I`, and noise matrix `nₜₕsin²(θ)I`.

## Example

```jldoctest
julia> attenuator(QuadPairBasis(1), pi/6, 3)
GaussianChannel for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
transform: 2×2 Matrix{Float64}:
 0.866025  0.0
 0.0       0.866025
noise: 2×2 Matrix{Float64}:
 0.75  0.0
 0.0   0.75
```
