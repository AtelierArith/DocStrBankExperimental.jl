```
add_edge_checked!([f!,], ict::IncrementalCycleTracker, v, w)
```

Using the incremental cycle tracker, ict, check whether adding the edge `v=>w` would introduce a cycle in the underlying graph. If so, return false and leave the ict intact. If not, update the underlying graph and return true.

# Optional `f!` Argument

By default the `add_edge!` function is used to update the underlying graph. However, for more complicated graphs, users may wish to manually specify the graph update operation. This may be accomplished by passing the optional `f!` callback argument. This callback is called on the underlying graph when no cycle is detected and is required to modify the underlying graph in order to effectuate the proposed edge addition.

# Batched edge additions

Optionally, either `v` or `w` (depending on the `in_out_reverse` flag) may be a collection of vertices representing a batched addition of vertices sharing a common source or target more efficiently than individual updates.

## Example

```jldoctest
julia> using Graphs

julia> G = SimpleDiGraph(3)
{3, 0} directed simple Int64 graph

julia> ict = IncrementalCycleTracker(G)
BFGT_N cycle tracker on SimpleDiGraph{Int64}(0, [Int64[], Int64[], Int64[]], [Int64[], Int64[], Int64[]])

julia> add_edge_checked!(ict, 1, 2)
true

julia> collect(edges(G))
1-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2

julia> add_edge_checked!(ict, 2, 3)
true

julia> collect(edges(G))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3

julia> add_edge_checked!(ict, 3, 1) # Would add a cycle
false

julia> collect(edges(G))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
```
