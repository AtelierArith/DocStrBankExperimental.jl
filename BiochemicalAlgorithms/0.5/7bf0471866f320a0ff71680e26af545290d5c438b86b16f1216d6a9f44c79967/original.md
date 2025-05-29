```
write_hinfile(
    fname::AbstractString,
    ac::AtomContainer
)
```

Save an atom container as HyperChem HIN file.

!!! note
    HIN files define molecules as connected components in the molecular graph. If the AtomContainer is missing bonds, e.g., after reading a PDB file and not postprocessing it correctly, the HIN file may contain a surprisingly large number of molecules.

