```
path_graph(n)
```

`n` 頂点を持つ無向 [path graph](https://en.wikipedia.org/wiki/Path_graph) を作成します。

# 例

```jldoctest
julia> path_graph(5)
{5, 4} 無向単純 Int64 グラフ

julia> path_graph(Int8(10))
{10, 9} 無向単純 Int8 グラフ
```
