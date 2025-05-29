```
UnstructuredMesh(g::CartesianMesh)
```

Convert `CartesianMesh` instance to unstructured grid. Note that the mesh must be 2D and 3D for a 1-to-1 conversion. 1D meshes are implicitly converted to 2D.
