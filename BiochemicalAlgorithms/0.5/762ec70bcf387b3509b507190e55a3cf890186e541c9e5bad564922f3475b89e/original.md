```
atoms(::Chain)
atoms(::Fragment)
atoms(::Molecule)
atoms(::System = default_system())
```

Returns an `AtomTable{T}` containing all atoms of the given atom container.

# Supported keyword arguments

  * `frame_id::MaybeInt = 1`
  * `molecule_idx::Union{MaybeInt, Some{Nothing}} = nothing`
  * `chain_idx::Union{MaybeInt, Some{Nothing}} = nothing`
  * `fragment_idx::Union{MaybeInt, Some{Nothing}} = nothing`

All keyword arguments limit the results to atoms matching the given IDs. Keyword arguments set to `nothing` are ignored. You can use `Some(nothing)` to explicitly filter for ID values of `nothing`.
