```
Mesh(faces[; views, attributes...])
Mesh(positions, faces[; views])
Mesh(positions, faces::AbstractVector{<: Integer}[; facetype = TriangleFace, skip = 1])
Mesh(; attributes...)
```

Constructs a mesh from the given arguments.

If `positions` are given explicitly, they are merged with other vertex attributes under the name `position`. Otherwise they must be part of `attributes`. If `faces` are not given `attributes.position` must be a FaceView.

Any other vertex attribute can be either an `AbstractVector` or a `FaceView` thereof. Every vertex attribute that is an `AbstractVector` must be sufficiently large to be indexable by `mesh.faces`. Every vertex attribute that is a `FaceView` must contain similar faces to `mesh.faces`, i.e. contain the same number of faces and have faces of matching length.

`views` can be defined optionally to implicitly split the mesh into multi sub-meshes. This is done by providing ranges for indexing faces which correspond to the sub-meshes. By default this is left empty.
