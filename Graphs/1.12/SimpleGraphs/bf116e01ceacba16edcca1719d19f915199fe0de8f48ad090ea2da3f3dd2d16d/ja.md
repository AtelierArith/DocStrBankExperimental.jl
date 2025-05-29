```
wheel_graph(n)
```

`n` 頂点を持つ無向 [ホイールグラフ](https://en.wikipedia.org/wiki/Wheel_graph) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> wheel_graph(5)
{5, 8} 無向単純 Int64 グラフ

julia> wheel_graph(Int8(6))
{6, 10} 無向単純 Int8 グラフ
```
