```
function MeshMaps.MeshMap(mesh::UniformBZMesh{T,DIM}, is_time_reversal::Bool=true, tol_symmetry=PointSymmetry.SYMMETRY_TOLERANCE)
```

与えられたUniformBZMeshに基づいて、ブリルアンゾーンの対称性に基づいてMeshMapを作成します。
