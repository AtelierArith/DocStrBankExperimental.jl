```
squeeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real)
squeeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real, noise::Ts)
```

Gaussian operator that squeezes the vacuum state into a squeezed state, known as the squeezing operator. The symplectic representation is given by `basis`. The amplitude and phase squeezing parameters  are given by `r` and `theta`, respectively. Noise can be added to the operation with `noise`.

## Mathematical description of a squeezing operator

A squeeze operator `S(r, θ)` is defined by the operation `S(r, θ)|0⟩ = |r, θ⟩`, where `r` and `θ` are the real amplitude and phase parameters,  respectively. The operator `S(r, θ)` is characterized by  the zero displacement vector and symplectic matrix `cosh(r)I - sinh(r)R(θ)`, where `R(θ)` is the rotation matrix.

## Example

```jldoctest
julia> squeeze(QuadPairBasis(1), 0.25, pi/4)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
symplectic: 2×2 Matrix{Float64}:
  0.852789  -0.178624
 -0.178624   1.21004
```
