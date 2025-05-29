Visualize a bipartite graph using Graphviz.

Works for both directed and undirected bipartite graphs. Both types of vertices in the bipartite graph become nodes in the Graphviz graph.

# Arguments

  * `prog="dot"`: Graphviz program to use
  * `graph_attrs`: Graph-level Graphviz attributes
  * `node_attrs`: Node-level Graphviz attributes
  * `edge_attrs`: Edge-level Graphviz attributes
  * `node_labels=false`: whether to label nodes and if so, which pair of data attributes to use
  * `edge_labels=false`: whether to label edges and if so, which data attribute (undirected case) or pair of attributes (directed case) to use
  * `invis_edge=true`: whether to add invisible edges between vertices of same type, which ensures that the order of the nodes is preserved.
