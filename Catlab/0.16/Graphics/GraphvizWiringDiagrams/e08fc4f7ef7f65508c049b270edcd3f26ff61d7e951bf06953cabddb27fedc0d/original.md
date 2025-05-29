Draw a wiring diagram using Graphviz.

The input can also be a morphism expression, in which case it is first converted into a wiring diagram. This function requires Graphviz v2.42 or higher.

# Arguments

  * `graph_name="G"`: name of Graphviz digraph
  * `orientation=TopToBottom`: orientation of layout. One of `LeftToRight`, `RightToLeft`, `TopToBottom`, or `BottomToTop`.
  * `node_labels=true`: whether to label the nodes
  * `labels=false`: whether to label the edges
  * `label_attr=:label`: what kind of edge label to use (if `labels` is true). One of `:label`, `:xlabel`, `:headlabel`, or `:taillabel`.
  * `port_size="24"`: minimum size of ports on box, in points
  * `junction_size="0.05"`: size of junction nodes, in inches
  * `outer_ports=true`: whether to display the outer box's input and output ports. If disabled, no incoming or outgoing wires will be shown either!
  * `anchor_outer_ports=true`: whether to enforce ordering of the outer box's input and output, i.e., ordering of the incoming and outgoing wires
  * `title::Union{Nothing, Graphviz.Label}=nothing: title of diagram
  * `graph_attrs=Dict()`: top-level graph attributes
  * `node_attrs=Dict()`: top-level node attributes
  * `edge_attrs=Dict()`: top-level edge attributes
  * `cell_attrs=Dict()`: main cell attributes in node HTML-like label
