```
EliminateGraph <: AbstractGraph
EliminateGraph(tbl::AbstractMatrix) -> EliminateGraph
```

A graph type for algorithms that involve node elimination. With this type, vertex elimination and recover do not allocate. `tbl` in the constructor is a boolean table for connection.
