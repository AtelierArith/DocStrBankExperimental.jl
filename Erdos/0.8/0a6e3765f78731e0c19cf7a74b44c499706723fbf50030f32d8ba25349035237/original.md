The generic multiroute_flow function will output three kinds of results:

  * When the number of routes is 0 or non-specified, the set of breaking points of

the multiroute flow is returned.

  * When the input is limited to a set of breaking points and a route value k,

only the value of the k-route flow is returned

  * Otherwise, a tuple with 1) the maximum flow and 2) the flow matrix. When the

max-flow subroutine is the Boykov-Kolmogorov algorithm, the associated mincut is returned as a third output.

When the input is a network, it requires the following arguments:

  * flow_graph::ADiGraph                   # the input graph
  * source::Int                           # the source vertex
  * target::Int                           # the target vertex
  * capacity_matrix::AbstractMatrix{T}  # edge flow capacities with T<:Real
  * flow_algorithm::AbstractFlowAlgorithm # keyword argument for flow algorithm
  * mrf_algorithm::AbstractFlowAlgorithm  # keyword argument for multiroute flow algorithm
  * routes::R<:Real                       # keyword argument for the number of routes

When the input is only the set of (breaking) points and the number of route, it requires the following arguments:

  * breakingpoints::Vector{Tuple{T, T, Int}},    # vector of breaking points
  * routes::R<:Real,                             # number of routes

When the input is the set of (breaking) points, the number of routes, and the network descriptors, it requires the following arguments:

  * breakingpoints::Vector{Tuple{T1, T1, Int}} # vector of breaking points (T1<:Real)
  * routes::R<:Real                            # number of routes
  * flow_graph::ADiGraph                        # the input graph
  * source::Int                                # the source vertex
  * target::Int                                # the target vertex
  * capacity_matrix::AbstractMatrix{T2}      # optional edge flow capacities (T2<:Real)
  * flow_algorithm::AbstractFlowAlgorithm      # keyword argument for algorithm

The function defaults to the Push-relabel (classical flow) and Kishimoto (multiroute) algorithms. Alternatively, the algorithms to be used can also be specified through  keyword arguments. A default capacity of 1 is assumed for each link if no capacity matrix is provided.

The mrf_algorithm keyword is inforced to Extended Multiroute Flow in the following cases:

  * The number of routes is non-integer
  * The number of routes is 0 or non-specified

### Usage Example :

(please consult the  max*flow section for options about flow*algorithm and capacity_matrix)

```julia

# Create a flow-graph and a capacity matrix
flow_graph = DiGraph(8)
flow_edges = [
    (1, 2, 10), (1, 3, 5),  (1, 4, 15), (2, 3, 4),  (2, 5, 9),
    (2, 6, 15), (3, 4, 4),  (3, 6, 8),  (4, 7, 16), (5, 6, 15),
    (5, 8, 10), (6, 7, 15), (6, 8, 10), (7, 3, 6),  (7, 8, 10)
]
capacity_matrix = zeros(Int, 8, 8)
for e in flow_edges
    u, v, f = e
    add_edge!(flow_graph, u, v)
    capacity_matrix[u, v] = f
end

# Run default multiroute_flow with an integer number of routes = 2
f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 2)

# Run default multiroute_flow with a noninteger number of routes = 1.5
f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 1.5)

# Run default multiroute_flow for all the breaking points values
points = multiroute_flow(flow_graph, 1, 8, capacity_matrix)
# Then run multiroute flow algorithm for any positive number of routes
f, F = multiroute_flow(points, 1.5)
f = multiroute_flow(points, 1.5, valueonly = true)

# Run multiroute flow algorithm using Boykov-Kolmogorov algorithm as max_flow routine
f, F, labels = multiroute_flow(flow_graph, 1, 8, capacity_matrix,
               algorithm = BoykovKolmogorovAlgorithm(), routes = 2)

```
