```
plot_graphviz(g, node_label= true, edge_label=false; path = zeros(Int, nv(mat))
```

グラフ `g` を `Graphviz` エンジンを使用して iJulia でレンダリングします。

#### 引数

  * `g::AbstractSimpleWeightedGraph`: エクスポートするグラフの表現
  * (オプション) `edge_label::Bool`: true の場合、すべてのエッジにその重みがラベル付けされます (デフォルト = false)
  * (オプション) `path = []`: ノードの Int-Array。ノードとそのエッジは赤色で描画されます (すなわち、最短経路)
  * (オプション) `colors = zeros(Int, nv(mat))`: Brewer カラースキームを使用してノードに色を付けます (最大 9 色)。
  * (オプション) `scale = 3.0`: プロットのスケール
  * (オプション) `landscape = false`: true の場合 > `rankdir` を `LR` に設定します
