```
merge_vertices(g::AbstractGraph, vs)
```

`vs`のすべての頂点が同じ頂点`minimum(vs)`にエイリアスされる新しいグラフを作成します。

# 例

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> collect(edges(g))
4-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
 Edge 4 => 5

julia> h = merge_vertices(g, [2, 3]);

julia> collect(edges(h))
3-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
```
