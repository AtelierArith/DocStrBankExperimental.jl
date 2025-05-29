```
TemporalSnapshotsGNNGraph(snapshots)
```

時間変化するグラフをスナップショットのシーケンスとして表す型であり、各スナップショットは[`GNNGraph`](@ref)です。

引数`snapshots`は、任意の数のノードとエッジを持つ`GNNGraph`のコレクションです。

時間的グラフを`tg`と呼ぶと、`tg[t]`は`t`-番目のスナップショットを返します。

スナップショットにはノード/エッジ/グラフの特徴を含めることができ、全体の時間的シーケンスのグローバルな特徴は`tg.tgdata`に保存できます。

スナップショットの追加と削除については、[`add_snapshot`](@ref)および[`remove_snapshot`](@ref)を参照してください。

# 例

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
