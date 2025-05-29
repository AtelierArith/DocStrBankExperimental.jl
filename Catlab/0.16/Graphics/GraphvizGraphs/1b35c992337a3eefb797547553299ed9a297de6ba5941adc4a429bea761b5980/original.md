Visualize a graph homomorphism using Graphviz.

Visualize a homomorphism (`ACSetTransformation`) between two graphs (instances of `AbstractGraph`). By default, the domain and codomain are drawn as subgraphs and the vertex mapping is drawn using dotted edges, whereas the edge map is suppressed. The vertex and edge mapping can also be shown using colors, via the `node_colors` and `edge_colors` keyword arguments.

# Arguments

  * `draw_codom=true`: whether to draw the codomain graph
  * `draw_mapping=true`: whether to draw the vertex mapping using edges
  * `prog="dot"`: Graphviz program to use
  * `graph_attrs`: Graph-level Graphviz attributes
  * `node_attrs`: Node-level Graphviz attributes
  * `edge_attrs`: Edge-level Graphviz attributes
  * `node_labels=false`: whether to draw node labels and which vertex attribute to use
  * `edge_labels=false`: whether to draw edge labels and which edge attribute to use
  * `node_colors=!draw_codom`: whether and how to color nodes based on vertex map
  * `edge_colors=!draw_codom`: whether and how to color edges based on edge map
