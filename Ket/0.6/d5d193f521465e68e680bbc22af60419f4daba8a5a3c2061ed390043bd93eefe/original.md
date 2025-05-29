```
applymap_subsystem(K::AbstractVector{<:AbstractSparseArray}, ρ::AbstractSparseArray, subsystems::AbstractVector{<:Integer}, dims::AbstractVector = _equal_sizes(ρ))
```

Applies the sparse Kraus operators in `K` to the subsytems of a sparse matrix `ρ` identified by `subsystems`, resulting in ∑ᵢ(K[i] ⊗ I) * ρ * (K[i]' ⊗ I). If the argument `dims` is omitted two equally-sized subsystems are assumed.
