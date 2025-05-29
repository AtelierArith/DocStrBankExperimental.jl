```
random_geometric_graph(n, radius; dim=2, pos=Nothing, embedding_metric=Nothing, dist_func=Nothing)
```

`n` 頂点を持つ [ランダム幾何グラフ](http://en.wikipedia.org/wiki/Random_geometric_graph) を作成します。頂点は、距離が `radius` より小さい場合に接続されます。頂点の位置は、各次元の単位区間から一様分布に従ってランダムに抽出されます。

参考文献: Penrose, Mathew. Random geometric graphs. Vol. 5. Oxford university press, 2003.

### オプション引数

  * `dim`: 埋め込み次元。デフォルトは dim=2 です。
  * `pos`: 頂点の位置は、`dim` 座標を持つ `n` 点のリストとして指定できます。デフォルトは pos=Nothing です。
  * `dist_func`: ランダム幾何グラフを構築するために使用される距離関数。独立したエッジの重みを許可するために、`eg` の `distance` 属性とは異なることがあります。`dist_func=Nothing` が渡された場合、デフォルトは `eg.distance` です。

# 例

```julia
julia> random_geometric_graph(50, 0.2).graph
{50, 105} undirected simple Int64 graph
```
