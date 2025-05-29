```
complete_digraph(n)
```

`n` 頂点を持つ有向 [完全グラフ](https://en.wikipedia.org/wiki/Complete_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> complete_digraph(5)
{5, 20} 有向単純 Int64 グラフ

julia> complete_digraph(Int8(6))
{6, 30} 有向単純 Int8 グラフ
```
