```
line_graph(G::AbstractGraph;
           vertex_labels::Array{Symbol, 1}=Symbol[])
```

'G'の線グラフを表すLabeledGraphを返します。

線グラフの各頂点のラベルは、'G'の対応する頂点のラベルを連結することによって作成されます。

配列`vertex_labels`のシンボルは、返される線グラフの頂点のラベルとして使用されます。`vertex_labels`が空である場合、ラベルは'G'の対応する頂点のインデックスを組み合わせることによって作成されます。
