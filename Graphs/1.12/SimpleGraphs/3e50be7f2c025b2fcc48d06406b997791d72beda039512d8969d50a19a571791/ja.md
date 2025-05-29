```
path_digraph(n)
```

`n` 頂点を持つ有向 [パスグラフ](https://en.wikipedia.org/wiki/Path_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> path_digraph(5)
{5, 4} directed simple Int64 graph

julia> path_digraph(Int8(10))
{10, 9} directed simple Int8 graph
```
