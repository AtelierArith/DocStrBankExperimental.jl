```
induced_subgraph(graph, nodes)
```

Generates a subgraph from the original graph using the provided `nodes`.  The function includes the nodes' neighbors and creates edges between nodes that are connected in the original graph.  If a node has no neighbors, an isolated node will be added to the subgraph.  Returns A new `GNNGraph` containing the subgraph with the specified nodes and their features.

# Arguments

  * `graph`. The original GNNGraph containing nodes, edges, and node features.
  * `nodes``. A vector of node indices to include in the subgraph.

# Examples

```julia
julia> s = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> t = [2, 3]
2-element Vector{Int64}:
 2
 3

julia> graph = GNNGraph((s, t), ndata = (; x=rand(Float32, 32, 3), y=rand(Float32, 3)), edata = rand(Float32, 2))
GNNGraph:
  num_nodes: 3
  num_edges: 2
  ndata:
        y = 3-element Vector{Float32}
        x = 32×3 Matrix{Float32}
  edata:
        e = 2-element Vector{Float32}

julia> nodes = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> subgraph = Graphs.induced_subgraph(graph, nodes)
GNNGraph:
  num_nodes: 2
  num_edges: 1
  ndata:
        y = 2-element Vector{Float32}
        x = 32×2 Matrix{Float32}
  edata:
        e = 1-element Vector{Float32}
```
