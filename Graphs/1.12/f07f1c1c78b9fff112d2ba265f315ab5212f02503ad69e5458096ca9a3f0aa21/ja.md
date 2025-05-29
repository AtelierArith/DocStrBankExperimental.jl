```
dijkstra_shortest_paths(g, srcs, distmx=weights(g));
```

グラフ上で[Dijkstraのアルゴリズム](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)を実行し、`srcs`と他のすべての頂点との間の最短距離を計算します。さまざまなトラバーサル情報を含む[`Graphs.DijkstraState`](@ref)を返します（`state.parents`や`state.dists`をクエリしてみてください）。

### オプション引数

  * `allpaths=false`: trueの場合、`state.pathcounts`は、ソースからその頂点までの最短経路の数を頂点でインデックス付けしたベクトルを保持します。ソース頂点の経路数は常に`1.0`です。到達できない頂点の経路数は常に`0.0`です。
  * `trackvertices=false`: trueの場合、`state.closest_vertices`は、最も近いものから最も遠いものまでの順にグラフ内のすべての頂点のベクトルを保持します。
  * `maxdist`（デフォルト: `typemax(T)`）は、すべての経路距離が無限であると見なされる最大経路距離を指定します（つまり、存在しないということです）。

### パフォーマンス

`distmx`にスパース行列を使用する場合、スパース転置の転置を渡すことでパフォーマンスが向上する可能性があります。つまり、`D`がスパース距離行列であると仮定すると：

```
D = transpose(sparse(transpose(D)))
```

`D`のスパース転置を実現することは重い一度限りのペナルティを伴うため、この戦略は距離行列を使って`dijkstra_shortest_paths`を複数回呼び出す予定がある場合にのみ使用するべきです。

# 例

```jldoctest
julia> using Graphs

julia> ds = dijkstra_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 2

julia> ds = dijkstra_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 3
```
