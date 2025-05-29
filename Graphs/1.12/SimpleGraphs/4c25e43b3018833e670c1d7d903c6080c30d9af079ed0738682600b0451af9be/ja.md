```
path_graph(n)
```

`n` 頂点を持つ無向 [パスグラフ](https://en.wikipedia.org/wiki/Path_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> path_graph(5)
{5, 4} undirected simple Int64 graph

julia> path_graph(Int8(10))
{10, 9} undirected simple Int8 graph
```
