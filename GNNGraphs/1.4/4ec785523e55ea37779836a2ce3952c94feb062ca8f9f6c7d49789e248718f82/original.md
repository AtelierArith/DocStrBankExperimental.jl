```
remove_edges(g::GNNGraph, edges_to_remove::AbstractVector{<:Integer})
remove_edges(g::GNNGraph, p=0.5)
```

Remove specified edges from a GNNGraph, either by specifying edge indices or by randomly removing edges with a given probability.

# Arguments

  * `g`: The input graph from which edges will be removed.
  * `edges_to_remove`: Vector of edge indices to be removed. This argument is only required for the first method.
  * `p`: Probability of removing each edge. This argument is only required for the second method and defaults to 0.5.

# Returns

A new GNNGraph with the specified edges removed.

# Example

```julia
julia> using GNNGraphs

# Construct a GNNGraph
julia> g = GNNGraph([1, 1, 2, 2, 3], [2, 3, 1, 3, 1])
GNNGraph:
  num_nodes: 3
  num_edges: 5
  
# Remove the second edge
julia> g_new = remove_edges(g, [2]);

julia> g_new
GNNGraph:
  num_nodes: 3
  num_edges: 4

# Remove edges with a probability of 0.5
julia> g_new = remove_edges(g, 0.5);

julia> g_new
GNNGraph:
  num_nodes: 3
  num_edges: 2
```
