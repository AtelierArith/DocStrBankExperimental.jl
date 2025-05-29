```
add_edge(
    graph::OptiGraph,
    nodes::OptiNode...;
    label=Symbol(graph.label, Symbol(".e"), length(graph.optiedges) + 1),
)
```

Add a new optiedge to `graph` that connects `nodes`. By default, the edge label is set to  be "e<i+1>" where "i" is the number of edges in the graph.
