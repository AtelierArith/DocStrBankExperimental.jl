```
badj(g::SimpleGraph[, v::Integer])
```

Return the backwards adjacency list of a graph. If `v` is specified, return only the adjacency list for that vertex.

###Implementation Notes Returns a reference to the current graph's internal structures, not a copy.  Do not modify result. If the graph is modified, the behavior is undefined:  the array behind this reference may be modified too, but this is not guaranteed.
