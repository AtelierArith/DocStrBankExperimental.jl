```
updatelocalpdb(; dir::AbstractString=pwd(), format::Type=PDBFormat)
```

Update a local copy of the Protein Data Bank (PDB).

Obtains the recent weekly lists of new, modified and obsolete PDB entries and automatically updates the PDB files of the given `format` inside the local `dir` directory. Requires an internet connection.
