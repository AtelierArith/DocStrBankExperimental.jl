```
expand_faceviews(mesh::Mesh)
```

Returns the given `mesh` if it contains no FaceViews. Otherwise, generates a new mesh that contains no FaceViews, reordering and duplicating vertex attributes as necessary. If the mesh has `views` they will be adjusted as needed to produce the same submeshes.
