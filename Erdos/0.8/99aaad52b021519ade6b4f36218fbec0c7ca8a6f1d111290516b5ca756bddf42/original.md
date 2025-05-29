```
add_edge!(g, e) -> (ok, new_edge)
```

Add to `g` the edge `e`.

```
add_edge!(g, u, v) -> (ok, new_edge)
```

Add to `g` an edge from `u` to `v`.

`ok=false` if add fails (e.g. if vertices are not in the graph or the edge is already present) and `true` otherwise. `new_edge` is the descriptor of the new edge.
