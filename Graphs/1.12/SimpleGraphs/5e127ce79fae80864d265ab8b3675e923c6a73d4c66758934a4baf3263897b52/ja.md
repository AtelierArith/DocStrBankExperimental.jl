```
star_graph(n)
```

`n` 頂点を持つ無向 [スターグラフ](https://en.wikipedia.org/wiki/Star_(graph_theory)) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> star_graph(3)
{3, 2} undirected simple Int64 graph

julia> star_graph(Int8(10))
{10, 9} undirected simple Int8 graph
```
