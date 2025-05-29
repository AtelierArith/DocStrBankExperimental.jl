```
run_EC_on_edges(dg, threshold_range; attribute = dg.edge_data.attributes[1], scale = false)
```

Returns the Euler Characteristic Curve by filtering the edges of the graph at each value in `threshold_range` and computing the Euler Characteristic after each filtration. If `attribute` is not defined, it defaults to the first attribute in the DataGraph's `EdgeData`. `scale` is a Boolean that indicates whether to scale the Euler Characteristic by the total number of objects (nodes + edges) in the original graph
