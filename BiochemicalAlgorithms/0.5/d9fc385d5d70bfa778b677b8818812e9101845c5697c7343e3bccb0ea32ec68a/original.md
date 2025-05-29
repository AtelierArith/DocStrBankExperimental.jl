```
fragments(::Chain)
fragments(::SecondaryStructure)
fragments(::Molecule)
fragments(::System = default_system())
```

Returns a `FragmentTable{T}` containing all fragments of the given atom container.

# Supported keyword arguments

  * `variant::Union{Nothing, FragmentVariantType} = nothing`
  * `molecule_idx::MaybeInt = nothing`
  * `chain_idx::MaybeInt = nothing`
  * `secondary_structure_idx::MaybeInt = nothing`

All keyword arguments limit the results to fragments matching the given IDs or variant type. Keyword arguments set to `nothing` are ignored.
