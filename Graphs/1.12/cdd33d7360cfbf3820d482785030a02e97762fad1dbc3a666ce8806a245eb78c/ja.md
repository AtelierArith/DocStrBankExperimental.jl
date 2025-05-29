```
is_ordered(e)
```

エッジ `e` の始点が終点以下であれば true を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = DiGraph(2);

julia> add_edge!(g, 2, 1);

julia> is_ordered(first(edges(g)))
false
```
