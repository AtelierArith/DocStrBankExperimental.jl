```
parent_system(::Atom)
parent_system(::Bond)
parent_system(::Chain)
parent_system(::SecondaryStructure)
parent_system(::Fragment)
parent_system(::Molecule)
parent_system(::System)
```

Returns the `System{T}` containing the given object. Alias for [`Base.parent`](@ref Base.parent(::System)).
