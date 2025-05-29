```
rand_temporal_radius_graph(number_nodes::Int, 
                           number_snapshots::Int,
                           speed::AbstractFloat,
                           r::AbstractFloat;
                           self_loops = false,
                           dir = :in,
                           kws...)
```

Create a random temporal graph given `number_nodes` nodes and `number_snapshots` snapshots. First, the positions of the nodes are randomly generated in the unit square. Two nodes are connected if their distance is less than a given radius `r`. Each following snapshot is obtained by applying the same construction to new positions obtained as follows. For each snapshot, the new positions of the points are determined by applying random independent displacement vectors to the previous positions. The direction of the displacement is chosen uniformly at random and its length is chosen uniformly in `[0, speed]`. Then the connections are recomputed. If a point happens to move outside the boundary, its position is updated as if it had bounced off the boundary.

# Arguments

  * `number_nodes`: The number of nodes of each snapshot.
  * `number_snapshots`: The number of snapshots.
  * `speed`: The speed to update the nodes.
  * `r`: The radius of connection.
  * `self_loops`: If `true`, consider the node itself among its neighbors, in which               case the graph will contain self-loops.
  * `dir`: The direction of the edges. If `dir=:in` edges go from the        neighbors to the central node. If `dir=:out` we have the opposite        direction.
  * `kws`: Further keyword arguments will be passed to the [`GNNGraph`](@ref) constructor of each snapshot.

# Example

```jldoctest
julia> n, snaps, s, r = 10, 5, 0.1, 1.5;

julia> tg = rand_temporal_radius_graph(n,snaps,s,r) # complete graph at each snapshot
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10, 10, 10]
  num_edges: [90, 90, 90, 90, 90]
  num_snapshots: 5
```
