```
random_geometric_graph!(eg, radius; dist_func=Nothing)
```

既存の埋め込み完全グラフ `eg` から、`radius` 以上離れた頂点間のエッジを削除することによって [ランダム幾何グラフ](http://en.wikipedia.org/wiki/Random_geometric_graph) を作成します。このインプレースグラフジェネレーターは、結果として得られる EmbeddedGraph インスタンス `eg` の特性に関してより柔軟性を提供します。たとえば、`weights(eg)` の値を決定する埋め込みメトリックは、ランダム幾何グラフを作成するために使用される距離関数 `dist_func` とは異なることができます。

参考文献: Penrose, Mathew. Random geometric graphs. Vol. 5. Oxford university press, 2003.

### オプション引数

  * `dist_func`: ランダム幾何グラフを構築するために使用される距離関数。独立したエッジの重みを許可するために、`eg` の `distance` 属性とは異なることができます。`dist_func=Nothing` が渡された場合、デフォルトで `eg.distance` になります。

# 例

```julia
julia> egh = EmbeddedGraph(complete_graph(n), pos, hamming);

julia> random_geometric_graph!(egh, rad; dist_func=euclidean)

julia> egh.graph
{50, 71} undirected simple Int64 graph
```
