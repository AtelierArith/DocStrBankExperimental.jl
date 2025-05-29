```
phaseshift([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, theta<:Real)
phaseshift([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, theta<:Real, noise::Ts)
```

Gaussian operator that rotates the phase of a given Gaussian mode by `theta`, as the phase shift operator. The symplectic representation is given by `basis`. Noise can be added to the operation with `noise`.

## Mathematical description of a phase shift operator

A phase shift operator is defined by the operation `U(θ) = exp(-iθâᵗâ)`, where `θ` is the phase parameter, and `âᵗ` and `â` are the raising and lowering operators, respectively. The operator `U(θ)` is characterized by  the zero displacement vector and symplectic matrix `[cos(θ) sin(θ); -sin(θ) cos(θ)]`.

## Example

```jldoctest
julia> phaseshift(QuadPairBasis(1), 3pi/4)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
symplectic: 2×2 Matrix{Float64}:
 -0.707107   0.707107
 -0.707107  -0.707107
```
