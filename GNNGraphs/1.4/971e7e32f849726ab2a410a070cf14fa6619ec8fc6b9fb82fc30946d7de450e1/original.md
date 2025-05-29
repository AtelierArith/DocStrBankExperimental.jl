```
add_snapshot(tg::TemporalSnapshotsGNNGraph, t::Int, g::GNNGraph)
```

Return a `TemporalSnapshotsGNNGraph` created starting from `tg` by adding the snapshot `g` at time index `t`.

# Examples

```jldoctest
julia> snapshots = [rand_graph(10, 20) for i in 1:5];

julia> tg = TemporalSnapshotsGNNGraph(snapshots)
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10, 10, 10]
  num_edges: [20, 20, 20, 20, 20]
  num_snapshots: 5

julia> new_tg = add_snapshot(tg, 3, rand_graph(10, 16)) # add a new snapshot at time 3
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10, 10, 10, 10]
  num_edges: [20, 20, 16, 20, 20, 20]
  num_snapshots: 6
```
