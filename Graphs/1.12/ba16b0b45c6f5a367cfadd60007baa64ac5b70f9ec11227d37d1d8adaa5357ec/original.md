```
eulerian(g::AbstractSimpleGraph{T}[, u::T]) --> T[]
```

Returns a [Eulerian trail or cycle](https://en.wikipedia.org/wiki/Eulerian_path) through an undirected graph `g`, starting at vertex `u`, returning a vector listing the vertices of `g` in the order that they are traversed. If no such trail or cycle exists, throws an error.

A Eulerian trail or cycle is a path that visits every edge of `g` exactly once; for a cycle, the path starts *and* ends at vertex `u`.

## Optional arguments

  * If `u` is omitted, a Eulerian trail or cycle is computed with `u = first(vertices(g))`.
