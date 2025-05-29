```
path_digraph(n)
```

`n` 頂点を持つ有向 [パスグラフ](https://en.wikipedia.org/wiki/Path_graph) を作成します。

# 例

```jldoctest
julia> path_digraph(5)
{5, 4} 有向単純 Int64 グラフ

julia> path_digraph(Int8(10))
{10, 9} 有向単純 Int8 グラフ
```
