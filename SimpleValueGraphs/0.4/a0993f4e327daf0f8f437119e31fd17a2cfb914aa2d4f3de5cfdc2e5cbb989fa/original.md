```
ValOutDiGraph{V = Int32}(n; vertexval_types=(), edgeval_types=(), vertexval_init=nothing, graphvals=())
ValOutDiGraph{V, V_VALS, E_VALS}(n; vertexval_init=nothing, graphvals=())
```

Construct a `ValOutDiGraph` with `n` vertices, zero edges and graph values `graphvals`.  The vertex value types are either `V_VALS` or `vertexval_types` and the edge value type are `edgeval_types`.

If omitted, the element type `V` is Int32.
