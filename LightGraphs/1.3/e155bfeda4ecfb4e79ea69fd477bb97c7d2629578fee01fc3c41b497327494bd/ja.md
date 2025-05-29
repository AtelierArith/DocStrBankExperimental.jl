```
desopo_pape_shortest_paths(g, src, distmx=weights(g))
```

ソース `src` とグラフ `g` の他のすべてのノード間の最短経路を [D'Esopo-Pape アルゴリズム](http://web.mit.edu/dimitrib/www/SLF.pdf) を使用して計算します。関連するトラバーサル情報を持つ [`LightGraphs.DEsopoPapeState`](@ref) を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> ds = desopo_pape_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Array{Int64,1}:
 1
 0
 1
 2
 2

julia> ds = desopo_pape_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Array{Int64,1}:
 1
 0
 1
 2
 3
```
