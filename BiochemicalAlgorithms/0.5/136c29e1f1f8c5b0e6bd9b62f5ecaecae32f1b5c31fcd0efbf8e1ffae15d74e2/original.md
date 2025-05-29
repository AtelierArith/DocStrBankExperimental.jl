```
SecondaryStructure{T} <: AbstractAtomContainer{T}
```

Mutable representation of an individual secondary structure element in a Chain.

# Public fields

  * `idx::Int`
  * `number::Int`
  * `type::SecondaryStructureType`
  * `name::String`

# Private fields

  * `properties::Properties`
  * `flags::Flags`
  * `molecule_idx::Int`
  * `chain_idx::Int`

# Constructors

```julia
SecondaryStructure(
    chain::Chain{T};
    number::Int,
    type::SecondaryStructureType;
    # keyword arguments
    name::AbstractString = "",
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `SecondaryStructure{T}` in the given chain.
