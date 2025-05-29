```
dst(e)
```

エッジ `e` の宛先頂点を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> dst(first(edges(g)))
2
```
