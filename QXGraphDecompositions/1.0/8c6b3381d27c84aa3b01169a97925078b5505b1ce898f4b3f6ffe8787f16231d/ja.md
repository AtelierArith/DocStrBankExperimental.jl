```
line_graph(G::AbstractGraph;
           vertex_labels::Array{Symbol, 1}=Symbol[])
```

'G' の線グラフを表す LabeledGraph を返します。

線グラフの各頂点のラベルは、'G' の対応する頂点のラベルを連結することによって作成されます。

配列 `vertex_labels` のシンボルは、返される線グラフの頂点のラベルとして使用されます。`vertex_labels` が空の場合、'G' の対応する頂点のインデックスを組み合わせることによってラベルが作成されます。
