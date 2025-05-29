```
TemporalSnapshotsGNNGraph(snapshots)
```

A type representing a time-varying graph as a sequence of snapshots, each snapshot being a [`GNNGraph`](@ref).

The argument `snapshots` is a collection of `GNNGraph`s with arbitrary  number of nodes and edges each. 

Calling `tg` the temporal graph, `tg[t]` returns the `t`-th snapshot.

The snapshots can contain node/edge/graph features, while global features for the whole temporal sequence can be stored in `tg.tgdata`.

See [`add_snapshot`](@ref) and [`remove_snapshot`](@ref) for adding and removing snapshots.

# Examples

```jldoctest
julia> snapshots = [rand_graph(i , 2*i) for i in 10:10:50];

julia> tg = TemporalSnapshotsGNNGraph(snapshots)
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 20, 30, 40, 50]
  num_edges: [20, 40, 60, 80, 100]
  num_snapshots: 5

julia> tg.num_snapshots
5

julia> tg.num_nodes
5-element Vector{Int64}:
 10
 20
 30
 40
 50

julia> tg[1]
GNNGraph:
  num_nodes: 10
  num_edges: 20

julia> tg[2:3]
TemporalSnapshotsGNNGraph:
  num_nodes: [20, 30]
  num_edges: [40, 60]
  num_snapshots: 2

julia> tg[1] = rand_graph(10, 16)
GNNGraph:
  num_nodes: 10
  num_edges: 16
```
