```
struct MeshField{V,M,B}
```

A field described by its discrete values on a mesh.

`Base.getindex` of an `MeshField` is overloaded to handle indices that lie outside the `CartesianIndices` of its `MeshField` by using `bcs`.
