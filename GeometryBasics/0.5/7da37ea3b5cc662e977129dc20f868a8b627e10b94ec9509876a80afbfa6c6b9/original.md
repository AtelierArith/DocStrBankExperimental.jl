```
split_mesh(mesh::Mesh, views::Vector{UnitRange{Int}} = mesh.views)
```

Creates a new mesh containing `faces(mesh)[range]` for each range in `views`. This also removes unused vertices.
