```
grid_topological_sort(g, s)
```

Apply the topological sort on an acyclic `GridGraph` `g`, and return a `ShortestPathTree` with source `s`.

Assumes vertex indices correspond to topological ranks. Compatible with ForwardDiff.
