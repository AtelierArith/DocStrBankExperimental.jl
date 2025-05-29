```
complete_graph(n)
```

`n` 頂点を持つ無向 [完全グラフ](https://en.wikipedia.org/wiki/Complete_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> complete_graph(5)
{5, 10} 無向単純 Int64 グラフ

julia> complete_graph(Int8(6))
{6, 15} 無向単純 Int8 グラフ
```
