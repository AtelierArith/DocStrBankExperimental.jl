```
PlasmoPlots.matrix_plot(
    graph::OptiGraph;
    node_labels=false,
    labelsize=24,
    subgraph_colors=false,
    node_colors=false,
    markersize=1,
    include_variable_constraints=false,
)
```

optigraph `graph` の行列ビジュアライゼーションをプロットします。行列ビジュアルをカスタマイズするために、次のキーワード引数を提供できます。

  * `node_labels = false`: 対応するオプティノードラベル属性を使用してノードにラベルを付けるかどうか。
  * `labelsize`: 各ノードラベルのサイズ。 `node_labels = true` の場合のみ有効です。
  * `subgraph_colors = false`: ノードをそのサブグラフに従って色付けするかどうか。
  * `node_colors = false`: ノードに色を付けるかどうか。 `subgraph_colors = false` の場合のみ有効です。
  * `markersize = 1`: 行列表現におけるリンク制約のサイズ。
  * `include_variable_constraints = false`: セット制約に変数を含めるかどうか。
