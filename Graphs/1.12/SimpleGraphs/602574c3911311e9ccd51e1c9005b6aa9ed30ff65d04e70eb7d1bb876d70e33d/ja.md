```
star_digraph(n)
```

`n` 頂点を持つ有向 [スターグラフ](https://en.wikipedia.org/wiki/Star_(graph_theory)) を作成します。

# 例

```jldoctest
julia> using Graphs

julia> star_digraph(3)
{3, 2} 有向単純 Int64 グラフ

julia> star_digraph(Int8(10))
{10, 9} 有向単純 Int8 グラフ
```
