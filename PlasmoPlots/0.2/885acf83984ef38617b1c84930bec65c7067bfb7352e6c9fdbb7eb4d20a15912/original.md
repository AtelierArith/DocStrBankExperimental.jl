```
PlasmoPlots.matrix_plot(
    graph::OptiGraph;
    node_labels=false,
    labelsize=24,
    subgraph_colors=false,
    node_colors=false,
    markersize=1,
    include_variable_constraints=false,
)
```

Plot a matrix visualization of the optigraph: `graph`. The following keyword arguments can be provided to customize the matrix visual.

  * `node_labels = false`: whether to label nodes using the corresponding optinode label attribute.
  * `labelsize`: the size for each node label.  Only active if `node_labels = true`.
  * `subgraph_colors = false`: whether to color nodes according to their subgraph.
  * `node_colors = false`: whether to color nodes.  Only active if `subgraph_colors = false`.
  * `markersize = 1`: Size of the linking constraints in the matrix representation.
  * `include_variable_constraints = false`: whether to include variable in set constraints
