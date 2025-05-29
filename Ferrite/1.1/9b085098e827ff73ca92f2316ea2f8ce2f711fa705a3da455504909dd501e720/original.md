```
addvertexset!(grid::AbstractGrid, name::String, faceid::AbstractVecOrSet{FaceIndex})
addvertexset!(grid::AbstractGrid, name::String, f::Function)
```

Adds a vertexset to the grid with key `name`. A vertexset maps a `String` key to a `OrderedSet` of tuples corresponding to `(global_cell_id, local_vertex_id)`. Vertexsets can be used to initialize `Dirichlet` boundary conditions for the `ConstraintHandler`.

```julia
addvertexset!(grid, "right", Set((VertexIndex(2,2), VertexIndex(4,2))))
addvertexset!(grid, "clamped", x -> norm(x[1]) ≈ 0.0)
```
