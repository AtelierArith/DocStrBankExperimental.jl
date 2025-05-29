```
maximum_flow(flow_graph, source, target[, capacity_matrix][, algorithm][, restriction])
```

Generic maximum*flow function for `flow*graph`from`source`to`target`with capacities in`capacity_matrix`. Uses flow algorithm`algorithm`and cutoff restriction`restriction`.

  * If `capacity_matrix` is not specified, `DefaultCapacity(flow_graph)` will be used.
  * If `algorithm` is not specified, it will default to [`PushRelabelAlgorithm`](@ref).
  * If `restriction` is not specified, it will default to `0`.

Return a tuple of (maximum flow, flow matrix). For the Boykov-Kolmogorov algorithm, the associated mincut is returned as a third output.

### Usage Example:

```julia
julia> flow_graph = Graphs.DiGraph(8) # Create a flow-graph
julia> flow_edges = [
(1,2,10),(1,3,5),(1,4,15),(2,3,4),(2,5,9),
(2,6,15),(3,4,4),(3,6,8),(4,7,16),(5,6,15),
(5,8,10),(6,7,15),(6,8,10),(7,3,6),(7,8,10)
]

julia> capacity_matrix = zeros(Int, 8, 8)  # Create a capacity matrix

julia> for e in flow_edges
    u, v, f = e
    Graphs.add_edge!(flow_graph, u, v)
    capacity_matrix[u,v] = f
end

julia> f, F = maximum_flow(flow_graph, 1, 8) # Run default maximum_flow (push-relabel) without the capacity_matrix

julia> f, F = maximum_flow(flow_graph, 1, 8, capacity_matrix) # Run default maximum_flow with the capacity_matrix

julia> f, F = maximum_flow(flow_graph, 1, 8, capacity_matrix, algorithm=EdmondsKarpAlgorithm()) # Run Edmonds-Karp algorithm

julia> f, F = maximum_flow(flow_graph, 1, 8, capacity_matrix, algorithm=DinicAlgorithm()) # Run Dinic's algorithm

julia> f, F, labels = maximum_flow(flow_graph, 1, 8, capacity_matrix, algorithm=BoykovKolmogorovAlgorithm()) # Run Boykov-Kolmogorov algorithm

```
