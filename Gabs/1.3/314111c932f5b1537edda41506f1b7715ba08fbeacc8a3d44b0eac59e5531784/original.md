```
vacuumstate([Tm=Vector{Float64}, Tc=Matrix{Float64}], basis::SymplecticBasis)
```

Gaussian state with zero photons, known as the vacuum state. The symplectic representation is defined by `basis`.

## Mathematical description of a vacuum state

A vacuum state `|0⟩` is characterized by the zero mean vector and covariance matrix `(ħ/2)I`.

## Example

```jldoctest
julia> vacuumstate(QuadPairBasis(1))
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
