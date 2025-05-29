```
cycle_graph(n)
```

`n` 頂点を持つ無向 [サイクルグラフ](https://en.wikipedia.org/wiki/Cycle_graph) を作成します。

# 例

```jldoctest
julia> cycle_graph(3)
{3, 3} 無向単純 Int64 グラフ

julia> cycle_graph(Int8(5))
{5, 5} 無向単純 Int8 グラフ
```
