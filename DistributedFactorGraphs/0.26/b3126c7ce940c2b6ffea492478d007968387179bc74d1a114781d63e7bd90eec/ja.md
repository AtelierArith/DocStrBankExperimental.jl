現在のところ、GraphDFGにのみ利用可能な特化型関数です。

ノート

  * 様々なタイプのフィルターのオプションがあります（メモリ使用量が増加します）

例

```julia
using IncrementalInference

# 例としての標準的なグラフ
fg = generateGraph_Kaess()

@show path = findShortestPathDijkstra(fg, :x1, :x3)
@show isVariable.(fg, path)
@show isFactor.(fg, path)
```

開発ノート

  * TODO 他のAbstractDFGエンティティに拡張する。
  * TODO フィルターのリソース消費の使用を改善できる。

関連

[`findFactorsBetweenNaive`](@ref), `Graphs.dijkstra_shortest_paths`
