```
src(e)
```

エッジ `e` の始点を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> src(first(edges(g)))
1
```
