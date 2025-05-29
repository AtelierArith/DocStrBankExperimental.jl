```
lollipop_graph(n1, n2)
```

サイズ `n1` のクリークとサイズ `n2` のパスがエッジで接続された [ロリポップグラフ](https://en.wikipedia.org/wiki/Lollipop_graph) を作成します。

### 実装ノート

`n1` と `n2` の eltype を保持します。必要な頂点数が eltype を超えるとエラーになります。`n1` と `n2` は、クリークとパスの両方に少なくとも1つの頂点があるために、少なくとも1でなければなりません。グラフは、ノード `1:n1` がクリークで、`n1+1:n1+n2` がパスとなるように構成されています。クリークはエッジ `(n1, n1+1)` でパスに接続されています。

# 例

```jldoctest
julia> using Graphs

julia> lollipop_graph(2, 5)
{7, 6} undirected simple Int64 graph

julia> lollipop_graph(Int8(3), Int8(4))
{7, 7} undirected simple Int8 graph
```
