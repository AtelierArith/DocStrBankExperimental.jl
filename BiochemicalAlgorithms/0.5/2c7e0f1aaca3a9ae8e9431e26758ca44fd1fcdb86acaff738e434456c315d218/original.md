```
residues(::Chain)
residues(::ChainTable)
residues(::SecondaryStructure)
residues(::SecondaryStructureTable)
residues(::Molecule)
residues(::MoleculeTable)
residues(::System = default_system())
```

Returns a `FragmentTable{T}` containing all [`FragmentVariant.Residue`](@ref FragmentVariant) fragments of the given atom container or table.

# Supported keyword arguments

See [`fragments`](@ref)
