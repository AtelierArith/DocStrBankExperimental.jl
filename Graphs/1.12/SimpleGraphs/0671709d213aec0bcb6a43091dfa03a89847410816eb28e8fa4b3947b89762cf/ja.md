```
wheel_digraph(n)
```

`n` 頂点を持つ有向 [ホイールグラフ](https://en.wikipedia.org/wiki/Wheel_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> wheel_digraph(5)
{5, 8} 有向単純 Int64 グラフ

julia> wheel_digraph(Int8(6))
{6, 10} 有向単純 Int8 グラフ
```
