```
convert_arguments(Mesh, xyz::AbstractVector)::GLNormalMesh
```

Takes an input mesh and a vector `xyz` representing the vertices of the mesh, and creates indices under the assumption, that each triplet in `xyz` forms a triangle.
