Draw an undirected wiring diagram using Graphviz.

Creates an undirected, bipartite Graphviz graph, with the boxes and outer ports of the diagram becoming nodes of one kind and the junctions of the diagram becoming nodes of the second kind.

# Arguments

  * `graph_name="G"`: name of Graphviz graph
  * `prog="neato"`: Graphviz program, usually "neato" or "fdp"
  * `box_labels=false`: if boolean, whether to label boxes with their number;  if a symbol, name of data attribute for box label
  * `port_labels=false`: whether to label ports with their number
  * `junction_labels=false`: if boolean, whether to label junctions with their number; if a symbol, name of data attribute for junction label
  * `junction_size="0.075"`: size of junction nodes, in inches
  * `implicit_junctions=false`: whether to represent a junction implicity as a wire when it has exactly two incident ports
  * `title::Union{Nothing, Graphviz.Label}=nothing: title of diagram
  * `graph_attrs=Dict()`: top-level graph attributes
  * `node_attrs=Dict()`: top-level node attributes
  * `edge_attrs=Dict()`: top-level edge attributes
