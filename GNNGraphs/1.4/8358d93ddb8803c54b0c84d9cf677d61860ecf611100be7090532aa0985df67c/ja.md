```
remove_snapshot(tg::TemporalSnapshotsGNNGraph, t::Int)
```

`tg`から時間インデックス`t`のスナップショットを削除して作成された[`TemporalSnapshotsGNNGraph`](@ref)を返します。

# 例

```jldoctest
julia> using GNNGraphs

julia> snapshots = [rand_graph(10,20), rand_graph(10,14), rand_graph(10,22)];

julia> tg = TemporalSnapshotsGNNGraph(snapshots)
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10]
  num_edges: [20, 14, 22]
  num_snapshots: 3

julia> new_tg = remove_snapshot(tg, 2) # 時間2のスナップショットを削除
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10]
  num_edges: [20, 22]
  num_snapshots: 2
```
