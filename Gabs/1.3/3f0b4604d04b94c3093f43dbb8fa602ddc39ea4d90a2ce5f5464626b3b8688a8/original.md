```
squeezedstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, r<:Real, theta<:Real)
```

Gaussian state with quantum uncertainty in its phase and amplitude, known as the squeezed state. The symplectic representation is defined by `basis`. The amplitude and phase squeezing parameters are given by `r` and `theta`, respectively.

## Mathematical description of a squeezed state

A squeezed state `|r, θ⟩`, where `r` is the amplitude squeezing parameter and `θ` is the phase squeezing parameter, is characterized by the zero mean vector and covariance matrix `(ħ/2) (cosh(2r)I - sinh(2r)R(θ))`, where `R(θ)` is the rotation matrix.

## Example

```jldoctest
julia> squeezedstate(QuadPairBasis(1), 0.5, pi/4)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
  0.712088  -0.830993
 -0.830993   2.37407
```
