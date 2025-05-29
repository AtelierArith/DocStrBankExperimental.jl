```
is_ordered(e)
```

エッジ `e` のソース頂点が宛先頂点以下であれば true を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = DiGraph(2);

julia> add_edge!(g, 2, 1);

julia> is_ordered(first(edges(g)))
false
```
