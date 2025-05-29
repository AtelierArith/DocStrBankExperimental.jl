```
merge_vertices(g::AbstractGraph, vs)
```

`vs`のすべての頂点が同じ頂点`minimum(vs)`にエイリアスされる新しいグラフを作成します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = path_graph(5);

julia> collect(edges(g))
4-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
 Edge 4 => 5

julia> h = merge_vertices(g, [2, 3]);

julia> collect(edges(h))
3-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
```
