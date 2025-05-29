```
write_mmcif(filename, atoms::AbstractVector{<:Atom}, [selection])
```

Write a mmCIF file with the atoms in `atoms` to `filename`. The optional `selection` argument is a string that can be used to select a subset of the atoms in `atoms`. For example, `write_mmcif(atoms, "test.cif", "name CA")`.
