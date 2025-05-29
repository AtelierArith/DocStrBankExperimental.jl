```
amplifier([Td=Vector{Float64}, Tt=Matrix{Float64},] basis::SymplecticBasis, r<:Real, n<:Int)
```

Gaussian channel describing the interaction of an input single mode Gaussian state and its environment via a two-mode squeezing operation. The channel is paramatrized by squeezing amplitude parameter `r` and thermal noise `n`.

## Mathematical description of an amplifier channel

An amplifier channel, `A(r, nₜₕ)`, where `r` is the squeezing amplitude parameter and `nₜₕ ≥ 1` is the thermal noise parameter, is characterized by the zero displacement vector, transformation matrix `cosh(r)I`, and noise matrix `nₜₕsinh²(r)I`.

## Example

```jldoctest
julia> amplifier(QuadPairBasis(1), 2.0, 3)
GaussianChannel for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
transform: 2×2 Matrix{Float64}:
 3.7622  0.0
 0.0     3.7622
noise: 2×2 Matrix{Float64}:
 39.4623   0.0
  0.0     39.4623
```
