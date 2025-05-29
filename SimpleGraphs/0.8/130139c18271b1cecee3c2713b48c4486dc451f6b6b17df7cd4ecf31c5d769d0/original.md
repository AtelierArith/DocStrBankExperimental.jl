`contract!(G,u,v)` contracts the edge `(u,v)` in the graph. The merged vertex is named `u` (hence `contract!(G,v,u)` results in a different, albeit isomorphic, graph).

Note: The edge `(u,v)` need not be present in the graph. If missing, this is equivalent to first adding the edge to the graph and then contracting it.
