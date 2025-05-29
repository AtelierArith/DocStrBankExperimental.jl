```
twosqueeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real)
twosqueeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real, noise::Ts)
```

Gaussian operator that squeezes a two-mode vacuum state into a two-mode squeezed state, known as the two-mode squeezing operator. The symplectic representation is given by `basis`. The amplitude and phase squeezing parameters  are given by `r` and `theta`, respectively. Noise can be added to the operation with `noise`.

## Mathematical description of a two-mode squeezing operator

A two-mode squeeze operator `S₂(r, θ)` is defined by the operation `S₂(r, θ)|0⟩ = |r, θ⟩`, where `r` and `θ` are the real amplitude and phase parameters, respectively. The operator  `S₂(r, θ)` is characterized by the zero displacement vector and symplectic matrix `[cosh(r)I -sinh(r)R(θ); -sinh(r)R(θ) cosh(r)I]`, where `R(θ)` is the rotation matrix.

## Example

```jldoctest
julia> twosqueeze(QuadPairBasis(2), 0.25, pi/4)
GaussianUnitary for 2 modes.
  symplectic basis: QuadPairBasis
displacement: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
symplectic: 4×4 Matrix{Float64}:
  1.03141    0.0       -0.178624  -0.178624
  0.0        1.03141   -0.178624   0.178624
 -0.178624  -0.178624   1.03141    0.0
 -0.178624   0.178624   0.0        1.03141
```
