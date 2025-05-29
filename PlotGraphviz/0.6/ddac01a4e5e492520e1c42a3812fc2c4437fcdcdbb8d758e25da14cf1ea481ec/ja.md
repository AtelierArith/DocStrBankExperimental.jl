```
write_dot_file(g, file; attributes, path, colors)
```

グラフ `g` をDOT形式にエクスポートし、ファイル `file` に保存します。

#### 引数

  * `g::AbstractSimpleWeightedGraph`: エクスポートするグラフの表現
  * `filename::AbstractString`: 保存するファイル名（例："graph.dot"）
  * （オプション）`attributes::AttributeDict`: ノードの色などのDot属性を辞書に格納
  * （オプション）`path = []`: ノードの整数配列。ノードとそのエッジは赤色で描画されます（例：最短経路）
  * （オプション）`colors = zeros(Int, nv(mat))`: 各ノードを色番号で表すコンポーネントカラーのベクトル。
