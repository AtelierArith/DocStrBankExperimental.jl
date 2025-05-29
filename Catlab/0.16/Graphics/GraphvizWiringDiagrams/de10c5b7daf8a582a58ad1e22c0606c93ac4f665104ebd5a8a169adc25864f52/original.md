Draw a circular port graph using Graphviz.

Creates a Graphviz graph. Ports are currently not respected in the image, but the port index for each box can be displayed to provide clarification.

# Arguments

  * `graph_name="G"`: name of Graphviz graph
  * `prog="neato"`: Graphviz program, usually "neato" or "fdp"
  * `box_labels=false`: whether to label boxes with their number
  * `port_labels=false`: whether to label ports with their number
  * `graph_attrs=Dict()`: top-level graph attributes
  * `node_attrs=Dict()`: top-level node attributes
  * `edge_attrs=Dict()`: top-level edge attributes

TODO: The lack of ports might be able to be resolved by introducing an extra node per port which is connected to its box with an edge of length 0.
