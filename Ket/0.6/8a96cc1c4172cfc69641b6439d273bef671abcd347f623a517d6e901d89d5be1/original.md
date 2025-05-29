```
applymap_subsystem(K::AbstractVector{<:AbstractMatrix}, ρ::AbstractMatrix, subsystems::Integer, dims::AbstractVector = _equal_sizes(ρ))
```

Applies the Kraus operators in `K` to the subsytem of `ρ` identified by `subsystems`, resulting in ∑ᵢ(K[i] ⊗ I) * ρ * (K[i]' ⊗ I). If the argument `dims` is omitted two equally-sized subsystems are assumed.
