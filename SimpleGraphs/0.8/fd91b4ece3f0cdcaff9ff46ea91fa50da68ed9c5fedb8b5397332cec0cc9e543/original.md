`add_edges!(G,edge_table)` adds edges to the graph `G`. The argument `edge_table` is an iterable list (array or set) of edges to be added (two-tuples). Returns the number of edges added to the graph.

This works both when `G` is a `UndirectedGraph` and when `G` is a `DirectedGraph`.
