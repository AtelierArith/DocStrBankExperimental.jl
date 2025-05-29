```
parent_molecule(::Atom)
parent_molecule(::Chain)
parent_molecule(::Fragment)
```

Returns the `Molecule{T}` containing the given object. Returns `nothing` if no such molecule exists.
