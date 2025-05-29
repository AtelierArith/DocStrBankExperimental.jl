```
TUDataset(name; dir=nothing)
```

さまざまなグラフベンチマークデータセット、*.e.g.* "QM9"、"IMDB-BINARY"、"REDDIT-BINARY"、または "PROTEINS" が、[TU Dortmund University](https://chrsmrrs.github.io/datasets/) から収集されています。TUDatasetコレクションからデータセット `name` を取得します。ここで `name` は、[こちら](https://chrsmrrs.github.io/datasets/docs/datasets/) で利用可能なデータセットのいずれかです。

`TUDataset` オブジェクトは、特定のグラフまたはグラフのサブセットを取得するためにインデックス指定できます。

フォーマットの詳細な説明については、[こちら](https://chrsmrrs.github.io/datasets/docs/format/) を参照してください。

# 使用例

```julia-repl
julia> data = TUDataset("PROTEINS")
dataset TUDataset:
  name        =>    PROTEINS
  metadata    =>    Dict{String, Any} with 1 entry
  graphs      =>    1113-element Vector{MLDatasets.Graph}
  graph_data  =>    (targets = "1113-element Vector{Int64}",)
  num_nodes   =>    43471
  num_edges   =>    162088
  num_graphs  =>    1113

julia> data[1]
(graphs = Graph(42, 162), targets = 1)
```
