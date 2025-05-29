```
turan_graph(n, r)
```

`n` 頂点と `r` 分割を持つ完全多部グラフである [Turán Graph](https://en.wikipedia.org/wiki/Tur%C3%A1n_graph) を作成します。

# 例

```jldoctest
julia> turan_graph(6, 2)
{6, 9} 無向単純 Int64 グラフ

julia> turan_graph(Int8(7), 2)
{7, 12} 無向単純 Int8 グラフ
```
