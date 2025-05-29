```
face_normals(positions::Vector{Point3{T}}, faces::Vector{<: NgonFace}[, target_type = Vec3{T}])
```

Compute face normals from the given `positions` and `faces` and returns an appropriate `FaceView`.
