```
nucleotides(::Chain)
nucleotides(::ChainTable)
nucleotides(::SecondaryStructure)
nucleotides(::SecondaryStructureTable)
nucleotides(::Molecule)
nucleotides(::MoleculeTable)
nucleotides(::System = default_system())
```

Returns a `FragmentTable{T}` containing all [`FragmentVariant.Nucleotide`](@ref FragmentVariant) fragments of the given atom container or table.

# Supported keyword arguments

See [`fragments`](@ref)
