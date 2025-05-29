```
cycle_graph(n)
```

`n` 頂点を持つ無向 [サイクルグラフ](https://en.wikipedia.org/wiki/Cycle_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> cycle_graph(3)
{3, 3} undirected simple Int64 graph

julia> cycle_graph(Int8(5))
{5, 5} undirected simple Int8 graph
```
