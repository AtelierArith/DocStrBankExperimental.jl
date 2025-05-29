```
Atom{T} <: AbstractSystemComponent{T}
```

Mutable representation of an individual atom in a system.

# Public fields

  * `idx::Int`
  * `number::Int`
  * `element::ElementType`
  * `name::String`
  * `atom_type::String`
  * `r::Vector3{T}`
  * `v::Vector3{T}`
  * `F::Vector3{T}`
  * `formal_charge::Int`
  * `charge::T`
  * `radius::T`

# Private fields

  * `properties::Properties`
  * `flags::Flags`
  * `frame_id::Int`
  * `molecule_idx::MaybeInt`
  * `chain_idx::MaybeInt`
  * `fragment_idx::MaybeInt`

# Constructors

```julia
Atom(
    ac::AbstractAtomContainer{T}
    number::Int,
    element::ElementType;
    # keyword arguments
    name::AbstractString = "",
    atom_type::AbstractString = "",
    r::Vector3{T} = Vector3{T}(0, 0, 0),
    v::Vector3{T} = Vector3{T}(0, 0, 0),
    F::Vector3{T} = Vector3{T}(0, 0, 0),
    formal_charge::Int = 0,
    charge::T = zero(T),
    radius::T = zero(T),
    properties::Properties = Properties(),
    flags::Flags = Flags(),
    frame_id::Int = 1
    molecule_idx::MaybeInt = nothing,
    chain_idx::MaybeInt = nothing,
    fragment_idx::MaybeInt = nothing
)
```

Creates a new `Atom{T}` in the given atom container.

```julia
Atom(
    number::Int,
    element::ElementType;
    kwargs...
)
```

Creates a new `Atom{Float32}` in the default system. Supports the same keyword arguments as above.
