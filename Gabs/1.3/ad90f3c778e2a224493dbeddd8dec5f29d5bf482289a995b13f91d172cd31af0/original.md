```
thermalstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, photons<:Int)
```

Gaussian state at thermal equilibrium, known as the thermal state. The symplectic representation is defined by `basis`. The mean photon number of the state is given by `photons`.

## Mathematical description of a thermal state

A thermal state `|n̄⟩`, where `n̄` is the mean number of photons, is characterized by the zero mean vector and covariance matrix `ħ(n̄+1/2)I`.

## Example

```jldoctest
julia> thermalstate(QuadPairBasis(1), 4)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
 9.0  0.0
 0.0  9.0
```
