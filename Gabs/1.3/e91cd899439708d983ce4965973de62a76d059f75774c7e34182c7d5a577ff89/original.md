```
displace([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, alpha<:Number)
displace([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, alpha<:Number, noise::Ts)
```

Gaussian operator that displaces the vacuum state into a coherent state, known as the displacement operator. The symplectic representation is given by `basis`. The complex amplitude is given by `alpha`. Noise can be added to the operation with `noise`.

## Mathematical description of a displacement operator

A displacement operator `D(α)` is defined by the operation `D(α)|0⟩ = |α⟩`, where `α` is a complex amplitude. The operator `D(α)`  is characterized by the displacement vector `√2ħ [real(α), imag(α)]`  and symplectic matrix `I`.

## Example

```jldoctest
julia> displace(QuadPairBasis(1), 1.0+im)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 2.0
symplectic: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
