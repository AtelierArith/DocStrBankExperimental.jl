```
WignerDrange(ℓₘₐₓ, m′ₘₐₓ=ℓₘₐₓ)
```

Create an array of (ℓ, m', m) indices as in 𝔇 array

See also [`WignerDsize`](@ref) and [`WignerDindex`](@ref).

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
