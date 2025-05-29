```
remove_multi_edges(g::GNNGraph; aggr=+)
```

Remove multiple edges (also called parallel edges or repeated edges) from graph `g`. Possible edge features are aggregated according to `aggr`, that can take value  `+`,`min`, `max` or `mean`.

See also [`remove_self_loops`](@ref), [`has_multi_edges`](@ref), and [`to_bidirected`](@ref).
