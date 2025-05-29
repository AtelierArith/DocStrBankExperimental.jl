```
split_mesh(mesh::Mesh, views::Vector{UnitRange{Int}} = mesh.views)
```

`faces(mesh)[range]`を各範囲の`views`に対して含む新しいメッシュを作成します。これにより、未使用の頂点も削除されます。
