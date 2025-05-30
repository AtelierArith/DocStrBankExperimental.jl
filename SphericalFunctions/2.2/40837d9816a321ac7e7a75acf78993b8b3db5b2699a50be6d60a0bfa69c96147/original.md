```
WignerHsize(ℓₘₐₓ, m′ₘₐₓ=ℓₘₐₓ)
```

Total size of array of wedges of width m′ₘₐₓ up to ℓₘₐₓ.  If m′ₘₐₓ is not given, it defaults to ℓₘₐₓ.

See also [`WignerHrange`](@ref) and [`WignerHindex`](@ref).

# Notes

Here, it is assumed that only data with m≥|m′| are stored, and only corresponding values are passed.  We also assume |m|≤ℓ and |m′|≤ℓ.  Neither of these are checked.  The wedge array that this function indexes is ordered as

```
[
    H(ℓ, m′, m) for ℓ ∈ 0:ℓₘₐₓ
    for m′ ∈ -min(ℓ, m′ₘₐₓ):min(ℓ, m′ₘₐₓ)
    for m ∈ abs(m′):ℓ
]
```
