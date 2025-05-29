```
bfs_parents(g, s[; dir=:out])
```

Perform a breadth-first search of graph `g` starting from vertex `s`. Return a vector of parent vertices indexed by vertex. If `dir` is specified, use the corresponding edge direction (`:in` and `:out` are acceptable values).

### Performance

This implementation is designed to perform well on large graphs. There are implementations which are marginally faster in practice for smaller graphs, but the performance improvements using this implementation on large graphs can be significant.
