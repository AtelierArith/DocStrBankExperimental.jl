```
weights(g)
```

Returns an edge map containing the "weights" associated to edges. For simple graphs, the return value is ConstEdgeMap(g, 1). For networks, returns the "weights" edge property if defined, otherwise the constant map.

Notice that the edge map returned by `weights` is the default value for the edge weights used in many flow and  distance on graph algorithms.
