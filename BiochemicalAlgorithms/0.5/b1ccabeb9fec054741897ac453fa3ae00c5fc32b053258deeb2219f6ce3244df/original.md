```
protein_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Molecule{T}
```

Returns the `Molecule{T}` associated with the given `idx` in `sys`. Throws a `KeyError` if no such molecule exists or if the molecule is not a [`MoleculeVariant.Protein`](@ref MoleculeVariant).
