```
face_normals(positions::Vector{Point3{T}}, faces::Vector{<: NgonFace}[, target_type = Vec3{T}])
```

与えられた `positions` と `faces` から面法線を計算し、適切な `FaceView` を返します。
