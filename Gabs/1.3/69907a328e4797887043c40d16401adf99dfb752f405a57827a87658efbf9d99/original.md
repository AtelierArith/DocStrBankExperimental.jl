```
eprstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, r<:Real, theta<:Real)
```

Gaussian state that is a two-mode squeezed state, known as the Einstein-Podolski-Rosen (EPR) state. The symplectic representation is defined by `basis`. The amplitude and phase squeezing parameters are given by `r` and `theta`, respectively.

## Mathematical description of an EPR state

An EPR state `|r, θ⟩ₑₚᵣ`, where `r` is the amplitude squeezing parameter and `θ` is the phase squeezing parameter, is characterized by the zero mean vector and covariance matrix `(ħ/2)[cosh(2r)I -sinh(2r)R(θ); -sinh(2r)R(θ) cosh(2r)I]`,  where `R(θ)` is the rotation matrix.

## Example

```jldoctest
julia> eprstate(QuadPairBasis(2), 0.5, pi/4)
GaussianState for 2 modes.
  symplectic basis: QuadPairBasis
mean: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
covariance: 4×4 Matrix{Float64}:
  1.54308    0.0       -0.830993  -0.830993
  0.0        1.54308   -0.830993   0.830993
 -0.830993  -0.830993   1.54308    0.0
 -0.830993   0.830993   0.0        1.54308
```
