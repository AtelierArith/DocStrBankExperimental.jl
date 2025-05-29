```
bonds(::Chain)
bonds(::Fragment)
bonds(::Molecule)
bonds(::System = default_system())
```

Returns a `BondTable{T}` containing all bonds of the given atom container where at least one associated atom is contained in the same container.

# Supported keyword arguments

See [`atoms`](@ref)
