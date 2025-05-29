```
HMatrix{T}(rowtree,coltree,adm)
```

Construct an empty `HMatrix` with `rowtree` and `coltree` using the admissibility condition `adm`. This function builds the skeleton for the hierarchical matrix, but **does not compute `data`** field in the blocks. See [`assemble_hmatrix`](@ref) for assembling a hierarhical matrix.
