```
edge_type_subgraph(g::GNNHeteroGraph, edge_ts)
```

`g`のサブグラフを返します。このサブグラフには、`edge_ts`のタイプのエッジのみが含まれます。エッジタイプは、単一のエッジタイプ（すなわち、3つのシンボルを含むタプル）またはエッジタイプのベクターとして指定できます。
