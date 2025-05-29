```
add_subgraph(graph::OptiGraph; name::Symbol=Symbol(:sg,gensym()))
```

Add an existing subgraph to an optigraph. The subgraph cannot already be part of another optigraph. It also should not have nodes that already exist in the optigraph.
