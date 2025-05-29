```
complete_bipartite_graph(n1, n2)
```

`n1 + n2` 頂点を持つ無向の [完全二部グラフ](https://en.wikipedia.org/wiki/Complete_bipartite_graph) を作成します。

# 例

```jldoctest
julia> complete_bipartite_graph(3, 4)
{7, 12} undirected simple Int64 graph

julia> complete_bipartite_graph(Int8(3), Int8(4))
{7, 12} undirected simple Int8 graph
```
