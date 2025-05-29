```
dag_longest_path(g, distmx=weights(g); topological_order=topological_sort_by_dfs(g))
```

Return a longest path within the directed acyclic graph `g`, with distance matrix `distmx` and using `topological_order` to iterate on vertices.
