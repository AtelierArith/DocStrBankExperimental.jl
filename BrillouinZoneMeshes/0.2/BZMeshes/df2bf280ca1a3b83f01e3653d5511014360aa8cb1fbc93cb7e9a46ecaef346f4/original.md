```
function MeshMaps.MeshMap(mesh::UniformBZMesh{T,DIM}, is_time_reversal::Bool=true, tol_symmetry=PointSymmetry.SYMMETRY_TOLERANCE)
```

create a MeshMap for the given UniformBZMesh based on the symmetry of the Brillouin zone.
