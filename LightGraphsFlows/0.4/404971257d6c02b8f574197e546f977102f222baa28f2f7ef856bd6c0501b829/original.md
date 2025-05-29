```
multiroute_flow(flow_graph, source, target[, DefaultCapacity][, flow_algorithm][, mrf_algorithm][, routes])
```

The generic multiroute_flow function.

The output will vary depending on the input:

  * When the number of `route`s is `0`, return the set of breaking points of

the multiroute flow.

  * When the number of `route`s is `1`, return a flow with a set of 1-disjoint paths

(this is the classical max-flow implementation).

  * When the input is limited to a set of breaking points and a route value `k`,

return only the k-route flow.

  * Otherwise, a tuple with 1) the maximum flow and 2) the flow matrix. When the

max-flow subroutine is the Boykov-Kolmogorov algorithm, the associated mincut is returned as a third output.

When the input is a network, it requires the following arguments:

  * `flow_graph`: the input graph
  * `source`: the source vertex
  * `target`: the target vertex
  * `capacity_matrix`: matrix of edge flow capacities
  * `flow_algorithm`: keyword argument for flow algorithm
  * `mrf_algorithm`: keyword argument for multiroute flow algorithm
  * `routes`: keyword argument for the number of routes

When the input is only the set of (breaking) points and the number of route, it requires the following arguments:

  * `breakingpoints`: vector of breaking points
  * `routes`: number of routes

When the input is the set of (breaking) points, the number of routes, and the network descriptors, it requires the following arguments:

  * `breakingpoints`: vector of breaking points
  * `routes`: number of routes
  * `flow_graph`: the input graph
  * `source`: the source vertex
  * `target`: the target vertex
  * `capacity_matrix`: matrix of edge flow capacities
  * `flow_algorithm`: keyword argument for flow algorithm

The function defaults to the Push-relabel (classical flow) and Kishimoto (multiroute) algorithms. Alternatively, the algorithms to be used can also be specified through  keyword arguments. A default capacity of `1` is assumed for each link if no capacity matrix is provided.

The `mrf_algorithm` keyword is inforced to Extended Multiroute Flow in the following cases:

  * The number of routes is non-integer
  * The number of routes is 0 or non-specified

### Usage Example :

(please consult the  [`maximum_flow`](@ref) section for options about flow*algorithm and capacity*matrix)

```julia
julia> flow_graph = lg.DiGraph(8) # Create a flow graph

julia> flow_edges = [
(1, 2, 10), (1, 3, 5),  (1, 4, 15), (2, 3, 4),  (2, 5, 9),
(2, 6, 15), (3, 4, 4),  (3, 6, 8),  (4, 7, 16), (5, 6, 15),
(5, 8, 10), (6, 7, 15), (6, 8, 10), (7, 3, 6),  (7, 8, 10)
]

julia> capacity_matrix = zeros(Int, 8, 8) # Create a capacity matrix

julia> for e in flow_edges
    u, v, f = e
    add_edge!(flow_graph, u, v)
    capacity_matrix[u, v] = f
end

julia> f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 2) # Run default multiroute_flow with an integer number of routes = 2

julia> f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 1.5) # Run default multiroute_flow with a noninteger number of routes = 1.5

julia> points = multiroute_flow(flow_graph, 1, 8, capacity_matrix) # Run default multiroute_flow for all the breaking points values

julia> f, F = multiroute_flow(points, 1.5) # Then run multiroute flow algorithm for any positive number of routes

julia> f = multiroute_flow(points, 1.5, valueonly = true)

julia> f, F, labels = multiroute_flow(flow_graph, 1, 8, capacity_matrix, algorithm = BoykovKolmogorovAlgorithm(), routes = 2) # Run multiroute flow algorithm using Boykov-Kolmogorov algorithm as maximum_flow routine

```
