```
nnucleotides(::Chain)
nnucleotides(::SecondaryStructure)
nnucleotides(::Molecule)
nnucleotides(::System = default_system())
```

Returns the number of [`FragmentVariant.Nucleotide`](@ref FragmentVariant) fragments in the given atom container.

# Supported keyword arguments

See [`fragments`](@ref)
