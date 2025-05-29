```
beamsplitter([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, transmit<:Real)
beamsplitter([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, transmit<:Real, noise::Ts)
```

Gaussian operator that serves as the beam splitter transformation of a two-mode Gaussian state, known as the beam splitter operator. The symplectic representation is given by `basis`. The transmittivity of the operator is given by `transmit`. Noise can be added to the operation with `noise`.

## Mathematical description of a beam splitter operator

A beam splitter operator `B(τ)` is defined by the operation `B(τ) = exp(θ(âᵗb̂ - âb̂ᵗ))`, where `θ` is defined by `τ = cos²θ`,  and `â` and `b̂` are the annihilation operators of the two modes,  respectively. The operator `B(τ)` is characterized by  the zero displacement vector and symplectic matrix `[√τI √(1-τ)I; -√(1-τ)I √τI]`.

## Example

```jldoctest
julia> beamsplitter(QuadPairBasis(2), 0.75)
GaussianUnitary for 2 modes.
  symplectic basis: QuadPairBasis
displacement: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
symplectic: 4×4 Matrix{Float64}:
  0.5        0.0       0.866025  0.0
  0.0        0.5       0.0       0.866025
 -0.866025   0.0       0.5       0.0
  0.0       -0.866025  0.0       0.5
```
