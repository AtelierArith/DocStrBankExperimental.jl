```
cycle_digraph(n)
```

`n` 頂点を持つ有向 [サイクルグラフ](https://en.wikipedia.org/wiki/Cycle_graph) を作成します。

# 例

```jldoctest
julia> cycle_digraph(3)
{3, 3} directed simple Int64 graph

julia> cycle_digraph(Int8(5))
{5, 5} directed simple Int8 graph
```
