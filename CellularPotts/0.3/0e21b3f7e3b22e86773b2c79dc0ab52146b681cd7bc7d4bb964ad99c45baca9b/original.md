```
VolumePenalty(λᵥ::Vector{Int})
```

A concrete type that penalizes cells that deviate from their desired volume.

Requires a vector `λᵥ` with n penalties where n is the number of cell types. `λᵥ` is zero-indexed meaning `λᵥ[0]` corresponds to the `:Medium` volume penalty (which is set to zero).

**Note**: `λᵥ` is automatically transformed to be a zero-indexed offset array and does not require the volume penalty for `:Medium`.
