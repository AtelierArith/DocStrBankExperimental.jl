```
dijkstra_shortest_paths(g, srcs, distmx=weights(g));
```

グラフ上で[Dijkstraのアルゴリズム](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)を実行し、`srcs`と他のすべての頂点との間の最短距離を計算します。さまざまなトラバーサル情報を含む[`LightGraphs.DijkstraState`](@ref)を返します。

### オプション引数

  * `allpaths=false`: trueの場合、特定の頂点のすべての前任者を追跡する[`LightGraphs.DijkstraState`](@ref)を返します。

### パフォーマンス

`distmx`にスパース行列を使用する場合、スパース転置の転置を渡すことでパフォーマンスが向上する可能性があります。つまり、`D`がスパース距離行列であると仮定すると:

```
D = transpose(sparse(transpose(D)))
```

`D`のスパース転置を実現することは重い一度限りのペナルティを伴うため、この戦略は距離行列を使って`dijkstra_shortest_paths`を複数回呼び出す予定がある場合にのみ使用するべきです。

# 例

```jldoctest
julia> using LightGraphs

julia> ds = dijkstra_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Array{Int64,1}:
 1
 0
 1
 2
 2

julia> ds = dijkstra_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Array{Int64,1}:
 1
 0
 1
 2
 3
```
