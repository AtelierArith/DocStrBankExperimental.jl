```julia
mutable struct System{T} <: BiochemicalAlgorithms.AbstractAtomContainer{T}
```

Mutable representation of a biomolecular system.

# Fields

  * `name::String`
  * `properties::Properties`
  * `flags::Flags`

# Constructors

```
System(name::AbstractString = "", properties::Properties = Properties(), flags::Flags = Flags())
```

Creates a new and empty `System{Float32}`.

```
System{T}(name::AbstractString = "", properties::Properties = Properties(), flags::Flags = Flags())
```

Creates a new and empty `System{T}`.
