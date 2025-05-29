```
rem_vertex!(g::SimpleWeightedDiGraph, v)
```

Remove the vertex `v` from graph `g`. Return false if removal fails (e.g., if vertex is not in the graph) and true otherwise.

!!! tip "Correctness"
    This operation has to be performed carefully if one keeps external data structures indexed by edges or vertices in the graph, since internally the removal results in all vertices with indices greater than `v` being shifted down one.

