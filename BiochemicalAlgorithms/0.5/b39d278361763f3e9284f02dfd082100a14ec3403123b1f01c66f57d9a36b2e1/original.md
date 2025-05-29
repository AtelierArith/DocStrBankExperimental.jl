```julia
secondary_structure_by_idx(
    sys::BiochemicalAlgorithms.System{T},
    idx::Int64
) -> BiochemicalAlgorithms.SecondaryStructure

```

Returns the `SecondaryStructure{T}` associated with the given `idx` in `sys`. Throws a `KeyError` if no such secondary structure exists.
