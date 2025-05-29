```
clique_graph(k, n)
```

`n` 個の接続された `k`-クリークからなるグラフを作成します。

# 例

```jldoctest
julia> clique_graph(4, 10)
{40, 70} 無向単純 Int64 グラフ

julia> clique_graph(Int8(10), Int8(4))
{40, 184} 無向単純 Int8 グラフ
```
