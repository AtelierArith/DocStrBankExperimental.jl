```
add_node(
    graph::OptiGraph; label=Symbol(graph.label, Symbol(".n"), length(graph.optinodes)+1
)
```

Add a new optinode to `graph`. By default, the node label is set to be "n<i+1>" where "i" is  the number of nodes in the graph.
