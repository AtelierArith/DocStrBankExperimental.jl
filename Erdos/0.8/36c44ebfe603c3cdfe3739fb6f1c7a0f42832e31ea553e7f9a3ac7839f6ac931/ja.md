```
dijkstra_shortest_paths(g, s, distmx=weights(g); allpaths=false)
dijkstra_shortest_paths(g, sources, distmx=weights(g); allpaths=false)
```

グラフに対して[Dijkstraのアルゴリズム](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)を実行し、ソース頂点`s`（またはベクトル`sources`）と他のすべての頂点との間の最短距離を計算します。さまざまなトラバーサル情報を含む`DijkstraState`を返します。

`allpaths=true`の場合、特定の頂点のすべての前任者を追跡する`DijkstraState`を返します。
