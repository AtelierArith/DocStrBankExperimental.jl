```
merge(meshes::AbstractVector{Mesh})
```

Generates a new mesh containing all the data of the individual meshes.

If all meshes are consistent in their use of FaceViews they will be preserved. Otherwise all of them will be converted with `expand_faceviews(mesh)`.

This function will generate `views` in the new mesh which correspond to the inputs of this function.
