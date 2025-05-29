```
remove_nodes(g::GNNGraph, nodes_to_remove::AbstractVector)
```

Remove specified nodes, and their associated edges, from a GNNGraph. This operation reindexes the remaining nodes to maintain a continuous sequence of node indices, starting from 1. Similarly, edges are reindexed to account for the removal of edges connected to the removed nodes.

# Arguments

  * `g`: The input graph from which nodes (and their edges) will be removed.
  * `nodes_to_remove`: Vector of node indices to be removed.

# Returns

A new GNNGraph with the specified nodes and all edges associated with these nodes removed. 

# Example

```julia
using GNNGraphs

g = GNNGraph([1, 1, 2, 2, 3], [2, 3, 1, 3, 1])

# Remove nodes with indices 2 and 3, for example
g_new = remove_nodes(g, [2, 3])

# g_new now does not contain nodes 2 and 3, and any edges that were connected to these nodes.
println(g_new)
```
