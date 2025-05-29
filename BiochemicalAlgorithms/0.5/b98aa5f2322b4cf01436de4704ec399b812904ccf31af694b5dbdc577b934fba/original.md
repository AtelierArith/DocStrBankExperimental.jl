```
Bond{T} <: AbstractAtomContainer{T}
```

Mutable representation of an individual bond in a system.

# Public fields

  * `idx::Int`
  * `a1::Int`
  * `a2::Int`
  * `order::BondOrderType`

# Private fields

  * `properties::Properties`
  * `flags::Flags`

# Constructors

```julia
Bond(
    ac::AbstractAtomContainer{T} = default_system(),
    a1::Int,
    a2::Int,
    order::BondOrderType;
    # keyword arguments
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Bond{T}` in the given (atom container's) system.

```julia
Bond(
    a1::Atom{T},
    a2::Atom{T},
    order::BondOrderType;
    # keyword arguments
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

Creates a new `Bond{T}` for the given atoms. Both atoms must belong to the same system.
