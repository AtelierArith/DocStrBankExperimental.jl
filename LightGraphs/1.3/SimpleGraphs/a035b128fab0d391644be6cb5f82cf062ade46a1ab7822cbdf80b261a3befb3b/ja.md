```
star_graph(n)
```

`n` 頂点を持つ無向 [スターグラフ](https://en.wikipedia.org/wiki/Star_(graph_theory)) を作成します。

# 例

```jldoctest
julia> star_graph(3)
{3, 2} 無向単純 Int64 グラフ

julia> star_graph(Int8(10))
{10, 9} 無向単純 Int8 グラフ
```
