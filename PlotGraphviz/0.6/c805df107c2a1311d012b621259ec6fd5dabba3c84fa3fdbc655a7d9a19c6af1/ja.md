```
plot_graphviz(g, attributes; path = zeros(Int, nv(mat)))
```

グラフ `g` を **iJulia** で `Graphviz` エンジンを使用してレンダリングします。

#### 引数

  * `g::AbstractSimpleWeightedGraph`: エクスポートするグラフ表現
  * `attributes::AttributeDict`: 独自のプロット属性セットでレンダリング (詳細は http://www.graphviz.org/ を参照)
  * (オプション) `path = []`: ノードの Int-Array。ノードとそのエッジは赤色で描画されます (すなわち最短経路)
  * (オプション) `colors = zeros(Int, nv(mat))`: Brewer カラースキームを使用してノードに色を付けます (最大 9 色)。
  * (オプション) `scale = 3.0`: プロットのスケールを設定します
  * (オプション) `landscape = false`: true の場合 > `rankdir` を `LR` に設定します
