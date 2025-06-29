```
function mincost_flow(g::AbstractGraph,
		node_demand::AbstractVector,
		edge_capacity::AbstractMatrix,
		edge_cost::AbstractMatrix,
		optimizer;
		edge_demand::Union{Nothing,AbstractMatrix} = nothing,
		source_nodes = (),
		sink_nodes = ()
		)
```

Find a flow over a directed graph `g` satisfying the `node_demand` at each node and `edge_capacity` constraints for each edge while minimizing `dot(edge_cost, flow)`.

Returns a sparse flow matrix, flow[i,j] corresponds to the flow on the (i,j) arc.

# Arguments

  * `g` is a directed `LightGraphs.AbstractGraph`.

-`node_demand` is a vector of nodal demand values, which should be negative for sources, positive for sink nodes, and zero for all other nodes.

  * `edge_capacity::AbstractMatrix` sets an upper bound on the flow of each arc.
  * `edge_cost::AbstractMatrix` the cost per unit of flow on each arc.
  * `optimizer` is an optimizer constructor, like `Clp.Optimizer` or `() -> Clp.Optimizer()` passed at the construction of the `JuMP.Model`.

# Keyword arguments

  * `edge_demand::Union{Nothing,AbstractMatrix}`: require a minimum flow for edges, or nothing.
  * `source_nodes` Collection of sources at which the nodal netflow is allowed to be greater than nodal demand, defaults to an empty tuple.
  * `sink_nodes` Collection of sinks at which the nodal netflow is allowed to be less than nodal demand, defaults to an empty tuple.

`source_nodes` & `sink_nodes` are only needed when nodal flow are not explictly set in node_demand

### Usage Example:

```julia
julia> import LightGraphs
julia> const LG = LightGraphs
julia> using LightGraphsFlows: mincost_flow
julia> import Clp # use your favorite LP solver here
julia> using SparseArrays: spzeros
julia> g = LG.DiGraph(6) # Create a flow-graph
julia> LG.add_edge!(g, 5, 1)
julia> LG.add_edge!(g, 5, 2)
julia> LG.add_edge!(g, 3, 6)
julia> LG.add_edge!(g, 4, 6)
julia> LG.add_edge!(g, 1, 3)
julia> LG.add_edge!(g, 1, 4)
julia> LG.add_edge!(g, 2, 3)
julia> LG.add_edge!(g, 2, 4)
julia> cost = zeros(6,6)
julia> cost[1,3] = 10
julia> cost[1,4] = 5
julia> cost[2,3] = 2
julia> cost[2,4] = 2
julia> demand = spzeros(6)
julia> demand[5] = -2
julia> demand[6] = 2
julia> capacity = ones(6,6)
julia> flow = mincost_flow(g, demand, capacity, cost, Clp.Optimizer)
```
