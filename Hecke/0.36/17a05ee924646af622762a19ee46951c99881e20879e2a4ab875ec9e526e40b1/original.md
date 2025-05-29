```
trace_lattice_with_isometry(H::HermLat, res::AbstractSpaceRes) where T
                                                   -> ZZLat, QQMatrix, AbstractSpaceRes
```

Return the trace lattice of `H` together with the associated isometry (see [`trace_lattice(::AbstractLat)`](@ref)) with respect to the given map of change of scalars `res`.
