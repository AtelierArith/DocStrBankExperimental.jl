```
convert_arguments(Mesh, x, y, z, indices)::GLNormalMesh
```

Takes real vectors x, y, z and constructs a triangle mesh out of those, using the faces in `indices`, which can be integers (every 3 -> one triangle), or GeometryBasics.NgonFace{N, <: Integer}.
