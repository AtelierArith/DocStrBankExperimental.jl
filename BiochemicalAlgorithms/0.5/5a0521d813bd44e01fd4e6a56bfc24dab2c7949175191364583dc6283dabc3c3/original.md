```
nbonds(::Chain)
nbonds(::Fragment)
nbonds(::Molecule)
nbonds(::System = default_system())
```

Returns the number of bonds in the given atom container where at least one associated atom is contained in the same container.

# Supported keyword arguments

See [`atoms`](@ref)
