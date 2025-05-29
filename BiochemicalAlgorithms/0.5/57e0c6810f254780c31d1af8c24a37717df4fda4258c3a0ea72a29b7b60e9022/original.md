```
Fragment{T} <: AbstractAtomContainer{T}
```

Mutable representation of an individual fragment in a system.

# Public fields

  * `idx::Int`
  * `number::Int`
  * `name::String`

# Private fields

  * `variant::FragmentVariantType`
  * `properties::Properties`
  * `flags::Flags`
  * `molecule_idx::Int`
  * `chain_idx::Int`
  * `secondary_structure_idx::Int`

# Constructors

```julia
Fragment(
    chain::Chain{T},
    number::Int;
    # keyword arguments
    name::AbstractString = "",
    variant::FragmentVariantType = FragmentVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Fragment{T}` in the given chain.

```julia
Fragment(
    secondary_structure::SecondaryStructure{T},
    number::Int;
    # keyword arguments
    name::AbstractString = "",
    variant::FragmentVariantType = FragmentVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Fragment{T}` in the given secondary structure.
