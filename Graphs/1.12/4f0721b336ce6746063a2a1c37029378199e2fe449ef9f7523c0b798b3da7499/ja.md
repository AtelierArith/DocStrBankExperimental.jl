```
desopo_pape_shortest_paths(g, src, distmx=weights(g))
```

グラフ `g` のソース `src` と他のすべてのノード間の最短経路を [D'Esopo-Pape アルゴリズム](http://web.mit.edu/dimitrib/www/SLF.pdf) を使用して計算します。関連するトラバーサル情報を持つ [`Graphs.DEsopoPapeState`](@ref) を返します（`state.parents` または `state.dists` をクエリしてみてください）。

# 例

```jldoctest
julia> using Graphs

julia> ds = desopo_pape_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 2

julia> ds = desopo_pape_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 3
```
