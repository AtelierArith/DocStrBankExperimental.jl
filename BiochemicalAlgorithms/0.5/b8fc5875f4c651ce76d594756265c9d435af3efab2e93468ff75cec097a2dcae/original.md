```
parent_secondary_structure(::Atom)
parent_secondary_structure(::Fragment)
parent_secondary_structure(::Nucleotide)
parent_secondary_structure(::Residue)
```

Returns the `SecondaryStructure{T}` containing the given object. Returns `nothing` if no such secondary structure exists.
