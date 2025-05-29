```
truncated_graph(g::PeriodicGraph)
```

Extract a simple graph from `g` by only keeping the edges that are strictly within the initial cell.

See also [`quotient_graph`](@ref) to keep all of these edges and [`slice_graph`](@ref) to keep only some of these edges.
