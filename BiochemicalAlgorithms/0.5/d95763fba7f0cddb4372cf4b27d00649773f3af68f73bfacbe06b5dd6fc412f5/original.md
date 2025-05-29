```
chains(::Molecule)
chains(::System = default_system(); kwargs...)
```

Returns a `ChainTable{T}` containing all chains of the given atom container.

# Supported keyword arguments

  * `molecule_idx::MaybeInt = nothing`: Any value other than `nothing` limits the result to chains belonging to the molecule with the given ID.
