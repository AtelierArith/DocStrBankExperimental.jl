```
has_vertex(g, v)
```

`v`が`g`の頂点である場合はtrueを返します。

# 例

```jldoctest
julia> using Graphs

julia> has_vertex(SimpleGraph(2), 1)
true

julia> has_vertex(SimpleGraph(2), 3)
false
```
