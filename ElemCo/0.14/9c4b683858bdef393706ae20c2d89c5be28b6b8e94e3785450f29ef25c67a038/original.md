```
@dummy(atoms)
```

Set atoms as dummy atoms in the system.   `atoms` is a list of atom indices or atomic symbols.

After running the macro, only the atoms in the list are set as dummy atoms in the system.

# Examples

```julia
@dummy [1,2,3]
@dummy ["H1","H2"]
@dummy [1,"H2",:H3]
@dummy [] # unset all dummy atoms
```
