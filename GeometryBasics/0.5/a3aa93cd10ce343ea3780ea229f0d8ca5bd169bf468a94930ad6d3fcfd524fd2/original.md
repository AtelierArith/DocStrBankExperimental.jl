```
normals(positions::Vector{Point3{T}}, faces::Vector{<: NgonFace}[; normaltype = Vec3{T}])
```

Compute vertex normals from the given `positions` and `faces`.

This runs through all faces, computing a face normal each and adding it to every involved vertex. The direction of the face normal is based on winding direction and assumed counter-clockwise faces. At the end the summed face normals are normalized again to produce a vertex normal.
