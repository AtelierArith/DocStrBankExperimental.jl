```
secondary_structures(::Molecule)
secondary_structures(::Chain)
secondary_structures(::System; kwargs...)
```

Returns a `SecondaryStructureTable{T}` containing all secondary structures of the given atom container.

# Supported keyword arguments

  * `molecule_idx::MaybeInt = nothing`
  * `chain_idx::MaybeInt = nothing`

All keyword arguments limit the results to secondary structures matching the given IDs. Keyword arguments set to `nothing` are ignored.
