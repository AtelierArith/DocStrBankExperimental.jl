```
refine_rg(m :: TriMesh)
```

Refine triangular mesh by subdivision of each edge into 2. Only triangles listed in `ind_red` are refined. Very slow for large meshes.
