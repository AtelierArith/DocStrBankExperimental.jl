```
WignerDindex(ℓ, m′, m, m′ₘₐₓ=ℓ)
```

Compute index into Wigner 𝔇 matrix

See also [`WignerDrange`](@ref) and [`WignerDsize`](@ref).

# Notes

This assumes that the Wigner 𝔇 matrix is arranged as

```
[
    𝔇(ℓ, m′, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m′ ∈ -min(ℓ, m′ₘₐₓ):min(ℓ, m′ₘₐₓ)
    for m ∈ -ℓ:ℓ
]
```
