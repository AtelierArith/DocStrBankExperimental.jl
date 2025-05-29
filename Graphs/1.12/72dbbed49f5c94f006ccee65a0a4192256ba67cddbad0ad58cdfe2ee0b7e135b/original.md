```
bfs_tree(g, s[; dir=:out])
```

Provide a breadth-first traversal of the graph `g` starting with source vertex `s`, and return a directed acyclic graph of vertices in the order they were discovered. If `dir` is specified, use the corresponding edge direction (`:in` and `:out` are acceptable values).
