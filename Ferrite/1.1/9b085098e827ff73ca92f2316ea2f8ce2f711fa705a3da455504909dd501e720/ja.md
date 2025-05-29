```
addvertexset!(grid::AbstractGrid, name::String, faceid::AbstractVecOrSet{FaceIndex})
addvertexset!(grid::AbstractGrid, name::String, f::Function)
```

グリッドにキー `name` を持つ vertexset を追加します。vertexset は `String` キーを `(global_cell_id, local_vertex_id)` に対応するタプルの `OrderedSet` にマッピングします。vertexset は `ConstraintHandler` のための `Dirichlet` 境界条件を初期化するために使用できます。

```julia
addvertexset!(grid, "right", Set((VertexIndex(2,2), VertexIndex(4,2))))
addvertexset!(grid, "clamped", x -> norm(x[1]) ≈ 0.0)
```
