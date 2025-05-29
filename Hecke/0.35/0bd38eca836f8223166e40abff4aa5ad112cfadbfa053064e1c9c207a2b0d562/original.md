```
trace_lattice_with_isometry_and_transfer_data(H::AbstractLat{T};
                                              alpha::FieldElem = one(base_field(H)),
                                              beta::FieldElem = gen(base_field(H)),
                                              order::Integer = 2) where T
                                                   -> ZZLat, QQMatrix, AbstractSpaceRes
```

Return the trace lattice of `H` together with the associated isometry corresponding to multiplication by `beta` (see [`trace_lattice(::AbstractLat)`](@ref)) and with the map of change of scalars associated to the underlying trace construction.
