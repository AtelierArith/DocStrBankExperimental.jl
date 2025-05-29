```
entanglement_entropy(ρ::AbstractMatrix, dims::AbstractVecOrTuple = _equal_sizes(ρ), n::Integer = 1; verbose = false)
```

Lower bounds the relative entropy of entanglement of a bipartite state `ρ` with subsystem dimensions `dims` using level `n` of the DPS hierarchy. If the argument `dims` is omitted equally-sized subsystems are assumed.
