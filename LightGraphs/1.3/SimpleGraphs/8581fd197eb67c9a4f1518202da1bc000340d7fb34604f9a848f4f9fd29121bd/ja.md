```
barbell_graph(n1, n2)
```

`n1`のサイズのクリークと`n2`のサイズのクリークがエッジで接続された[バーベルグラフ](https://en.wikipedia.org/wiki/Barbell_graph)を作成します。

### 実装ノート

`n1`と`n2`のeltypeを保持します。必要な頂点数がeltypeを超える場合はエラーになります。`n1`と`n2`は両方のクリークが空でないように少なくとも1でなければなりません。クリークは、ノード`1:n1`が左のクリーク、`n1+1:n1+n2`が右のクリークとして整理されます。クリークはエッジ`(n1, n1+1)`で接続されています。

# 例

```jldoctest
julia> barbell_graph(3, 4)
{7, 10} undirected simple Int64 graph

julia> barbell_graph(Int8(5), Int8(5))
{10, 21} undirected simple Int8 graph
```
