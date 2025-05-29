```
MetaGraph(
    graph,
    vertices_description,
    edges_description,
    graph_data=nothing,
    weight_function=edge_data -> 1.0,
    default_weight=1.0,
)
```

非空の `graph` に基づいて、指定された頂点および辺のデータを持つ非空の `MetaGraph` を構築します。*位置引数として与えられます*。

データは以下のように与えられなければなりません：

  * `vertices_description` はペア `label => data` のベクトルです（頂点のコードはリスト内のそのランクに対応します）
  * `edges_description` はペア `(label1, label2) => data` のベクトルです

さらに、これらの引数は `graph` 引数と整合性がなければならず、同じ頂点と辺のセットを記述する必要があります。
