```
FaceView(data, faces)
```

A FaceView is an alternative to passing a vertex attribute directly to a mesh. It bundles `data` with a new set of `faces` which may index that data differently from the faces defined in a mesh. This can be useful to avoid duplication in `data`.

For example, `data` can be defined per face by giving each face just one (repeated) index:

```julia
per_face_normals = FaceView(
    normals,                 # one per face
    FT.(eachindex(normals))  # with FT = facetype(mesh)
)
```

If you need a mesh with strictly per-vertex data, e.g. for rendering, you can use `expand_faceviews(mesh)` to convert every vertex attribute to be per-vertex. This will duplicate data and reorder faces as needed.

You can get the data of a FaceView with `values(faceview)` and the faces with `faces(faceview)`.
