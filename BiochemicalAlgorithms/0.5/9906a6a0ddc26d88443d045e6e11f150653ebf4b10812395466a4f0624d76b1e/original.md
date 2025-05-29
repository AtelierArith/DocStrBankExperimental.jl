```
nresidues(::Chain)
nresidues(::SecondaryStructure)
nresidues(::Molecule)
nresidues(::System = default_system())
```

Returns the number of [`FragmentVariant.Residue`](@ref FragmentVariant) fragments in the given atom container.

# Supported keyword arguments

See [`fragments`](@ref)
