```
applymap_subsystem(op::AbstractMatrix, ψ::AbstractVector, subsystems::AbstractVector, dims::AbstractVector = _equal_sizes(ρ))
```

Applies the operator `op` to the subsytem of `ρ` identified by `subsystems`, resulting in (op ⊗ I) * ψ. If the argument `dims` is omitted two equally-sized subsystems are assumed.
