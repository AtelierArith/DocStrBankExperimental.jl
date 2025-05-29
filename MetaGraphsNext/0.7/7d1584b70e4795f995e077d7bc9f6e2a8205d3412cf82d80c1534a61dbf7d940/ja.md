```
MetaGraph(
    graph;
    label_type,
    vertex_data_type=Nothing,
    edge_data_type=Nothing,
    graph_data=nothing,
    weight_function=edge_data -> 1.0,
    default_weight=1.0
)
```

空の `graph` に基づいて空の `MetaGraph` を構築し、メタデータタイプをキーワード引数として初期化します。

!!! warning
    このコンストラクタは便利さのためにキーワード引数を使用しているため、型が不安定です。

