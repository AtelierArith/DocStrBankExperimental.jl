```
has_path(g::AbstractGraph, u, v; exclude_vertices=Vector())
```

Return `true` if there is a path from `u` to `v` in `g` (while avoiding vertices in `exclude_vertices`) or `u == v`. Return false if there is no such path or if `u` or `v` is in `excluded_vertices`. 
