```
ladder_graph(n)
```

`2n` ノードと `3n-2` エッジからなる [ラダーグラフ](https://en.wikipedia.org/wiki/Ladder_graph) を作成します。

### 実装ノート

`n` の eltype を保持します。必要な頂点数が eltype を超える場合はエラーになります。

# 例

```jldoctest
julia> ladder_graph(3)
{6, 7} undirected simple Int64 graph

julia> ladder_graph(Int8(4))
{8, 10} undirected simple Int8 graph
```
