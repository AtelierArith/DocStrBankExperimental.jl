```
parent_protein(::Atom)
parent_protein(::Chain)
parent_protein(::Fragment)
```

Returns the `Molecule{T}` containing the given object. Returns `nothing` if no such molecule exists or if the molecule is not a [`MoleculeVariant.Protein`](@ref MoleculeVariant).
