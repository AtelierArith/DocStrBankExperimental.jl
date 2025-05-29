```
adjacency_list(g; dir=:out)
adjacency_list(g, nodes; dir=:out)
```

Return the adjacency list representation (a vector of vectors) of the graph `g`.

Calling `a` the adjacency list, if `dir=:out` than `a[i]` will contain the neighbors of node `i` through outgoing edges. If `dir=:in`, it will contain neighbors from incoming edges instead.

If `nodes` is given, return the neighborhood of the nodes in `nodes` only.
