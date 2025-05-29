```
run_EC_on_nodes(dg, threshold_range; attribute = dg.node_data.attributes[1], scale = false)
```

Returns the Euler Characteristic Curve by filtering the nodes of the graph at each value in `threshold_range` and computing the Euler Characteristic after each filtration. If `attribute` is not defined, it defaults to the first attribute in the DataGraph's `NodeData`. `scale` is a Boolean that indicates whether to scale the Euler Characteristic by the total number of objects (nodes + edges) in the original graph
