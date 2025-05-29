```
aggregate(graph::OptiGraph; name=gensym())
```

Aggregate an optigraph into a graph containing a single optinode. An optional  `name` can be used to name the new optigraph. Returns the new optinode (which points to a new graph with `source_graph(node)`) and a  mapping from the original graph variables and constraints to the new node variables and  constraints.
