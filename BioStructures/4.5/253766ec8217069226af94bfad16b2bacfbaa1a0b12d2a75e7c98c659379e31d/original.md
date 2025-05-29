```
runstride!(struc)
runstride!(model)
```

Run STRIDE on the given structural element to assign secondary structure.

Requires the STRIDE_jll.jl package to be imported. A temporary PDB file is written, so this will fail if the structural element cannot be written to a PDB file, for example if there are two-letter chain IDs.
