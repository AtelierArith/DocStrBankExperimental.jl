```
src(e)
```

エッジ `e` のソース頂点を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> src(first(edges(g)))
1
```
