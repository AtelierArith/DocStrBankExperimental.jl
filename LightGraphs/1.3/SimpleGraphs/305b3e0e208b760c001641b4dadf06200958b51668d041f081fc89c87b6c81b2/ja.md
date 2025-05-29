```
star_digraph(n)
```

`n` 頂点を持つ有向 [スターグラフ](https://en.wikipedia.org/wiki/Star_(graph_theory)) を作成します。

# 例

```jldoctest
julia> star_digraph(3)
{3, 2} directed simple Int64 graph

julia> star_digraph(Int8(10))
{10, 9} directed simple Int8 graph
```
