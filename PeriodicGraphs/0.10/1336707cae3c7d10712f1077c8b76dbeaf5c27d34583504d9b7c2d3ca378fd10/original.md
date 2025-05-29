```
quotient_graph(g::PeriodicGraph)
```

Extract a simple graph from `g` by removing all indications of offset in the edges. This means that edges that used to cross the boundaries of the initial cell now bind the source vertex to the representative of the destination vertex that is in the initial cell.

Note that these modified edges may turn into loops.

See also [`truncated_graph`](@ref) to remove all of these edges and [`slice_graph`](@ref) to keep only some of these edges.
