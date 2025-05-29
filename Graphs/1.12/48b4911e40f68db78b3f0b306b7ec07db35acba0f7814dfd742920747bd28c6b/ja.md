```
reverse(e)
```

ソースとデスティネーションの頂点が逆になった新しいエッジを `e` から作成します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph(2);

julia> add_edge!(g, 1, 2);

julia> reverse(first(edges(g)))
Edge 2 => 1
```
