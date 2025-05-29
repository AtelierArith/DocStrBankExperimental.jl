```
Molecule{T} <: AbstractAtomContainer{T}
```

Mutable representation of an individual molecule in a system.

# Public fields

  * `idx::Int`
  * `name::String`

# Private fields

  * `variant::MoleculeVariantType`
  * `properties::Properties`
  * `flags::Flags`

# Constructors

```julia
Molecule(
    sys::System{T};
    # keyword arguments
    name::AbstractString = "",
    variant::MoleculeVariantType = MoleculeVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Molecule{T}` in the given system.

```julia
Molecule(;
    #keyword arguments
    name::AbstractString = "",
    variant::MoleculeVariantType = MoleculeVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Molecule{Float32}` in the default system.
