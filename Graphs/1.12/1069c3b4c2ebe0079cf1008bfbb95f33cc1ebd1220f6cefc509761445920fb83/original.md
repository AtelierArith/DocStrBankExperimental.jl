```
dfs_parents(g, s[; dir=:out])
```

Perform a depth-first search of graph `g` starting from vertex `s`. Return a vector of parent vertices indexed by vertex. If `dir` is specified, use the corresponding edge direction (`:in` and `:out` are acceptable values).

### Implementation Notes

This version of DFS is iterative.
