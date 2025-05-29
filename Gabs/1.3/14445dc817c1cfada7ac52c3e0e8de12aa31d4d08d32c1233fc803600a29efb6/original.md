```
coherentstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, alpha<:Number)
```

Gaussian state that is the quantum analogue of a monochromatic electromagnetic field, known as the coherent state. The symplectic representation is defined by `basis`. The complex amplitude of the state is given by `alpha`.

## Mathematical description of a coherent state

A coherent state `|α⟩`, where `α` is the complex amplitude, is characterized by the mean vector `√2ħ [real(α), imag(α)]` and covariance matrix `(ħ/2)I`.

## Example

```jldoctest
julia> coherentstate(QuadPairBasis(1), 1.0+im)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 2.0
 2.0
covariance: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
