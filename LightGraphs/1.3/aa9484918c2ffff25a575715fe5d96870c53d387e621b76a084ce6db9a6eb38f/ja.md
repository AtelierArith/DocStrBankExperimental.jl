```
has_vertex(g, v)
```

`v` が `g` の頂点である場合は true を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> has_vertex(SimpleGraph(2), 1)
true

julia> has_vertex(SimpleGraph(2), 3)
false
```
