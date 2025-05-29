```
remove_snapshot(tg::TemporalSnapshotsGNNGraph, t::Int)
```

Return a [`TemporalSnapshotsGNNGraph`](@ref) created starting from `tg` by removing the snapshot at time index `t`.

# Examples

```jldoctest
julia> using GNNGraphs

julia> snapshots = [rand_graph(10,20), rand_graph(10,14), rand_graph(10,22)];

julia> tg = TemporalSnapshotsGNNGraph(snapshots)
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10]
  num_edges: [20, 14, 22]
  num_snapshots: 3

julia> new_tg = remove_snapshot(tg, 2) # remove snapshot at time 2
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10]
  num_edges: [20, 22]
  num_snapshots: 2
```
