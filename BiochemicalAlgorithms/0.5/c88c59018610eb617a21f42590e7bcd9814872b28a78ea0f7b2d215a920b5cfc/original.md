```
Chain{T} <: AbstractAtomContainer{T}
```

Mutable representation of an individual chain in a system.

# Public fields

  * `idx::Int`
  * `name::String`

# Private fields

  * `properties::Properties`
  * `flags::Flags`
  * `molecule_idx::Int`

# Constructors

```julia
Chain(
    mol::Molecule{T};
    # keyword arguments
    name::AbstractString = "",
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Chain{T}` in the given molecule.
