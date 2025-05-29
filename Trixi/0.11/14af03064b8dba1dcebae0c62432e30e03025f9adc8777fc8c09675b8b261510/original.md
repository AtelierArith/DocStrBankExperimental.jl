```
DGMultiMesh{NDIMS, ...}
```

`DGMultiMesh` describes a mesh type which wraps `StartUpDG.MeshData` and `boundary_faces` in a dispatchable type. This is intended to store geometric data and connectivities for any type of mesh (Cartesian, affine, curved, structured/unstructured).
