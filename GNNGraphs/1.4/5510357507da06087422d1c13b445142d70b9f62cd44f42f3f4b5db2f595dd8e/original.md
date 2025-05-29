```
sample_neighbors(g, nodes, K=-1; dir=:in, replace=false, dropnodes=false)
```

Sample neighboring edges of the given nodes and return the induced subgraph. For each node, a number of inbound (or outbound when `dir = :out``) edges will be randomly chosen.  If`dropnodes=false`, the graph returned will then contain all the nodes in the original graph,  but only the sampled edges.

The returned graph will contain an edge feature `EID` corresponding to the id of the edge in the original graph. If `dropnodes=true`, it will also contain a node feature `NID` with the node ids in the original graph.

# Arguments

  * `g`. The graph.
  * `nodes`. A list of node IDs to sample neighbors from.
  * `K`. The maximum number of edges to be sampled for each node.      If -1, all the neighboring edges will be selected.
  * `dir`. Determines whether to sample inbound (`:in`) or outbound (``:out`) edges (Default `:in`).
  * `replace`. If `true`, sample with replacement.
  * `dropnodes`. If `true`, the resulting subgraph will contain only the nodes involved in the sampled edges.

# Examples

```julia
julia> g = rand_graph(20, 100)
GNNGraph:
    num_nodes = 20
    num_edges = 100

julia> sample_neighbors(g, 2:3)
GNNGraph:
    num_nodes = 20
    num_edges = 9
    edata:
        EID => (9,)

julia> sg = sample_neighbors(g, 2:3, dropnodes=true)
GNNGraph:
    num_nodes = 10
    num_edges = 9
    ndata:
        NID => (10,)
    edata:
        EID => (9,)

julia> sg.ndata.NID
10-element Vector{Int64}:
  2
  3
 17
 14
 18
 15
 16
 20
  7
 10

julia> sample_neighbors(g, 2:3, 5, replace=true)
GNNGraph:
    num_nodes = 20
    num_edges = 10
    edata:
        EID => (10,)
```
