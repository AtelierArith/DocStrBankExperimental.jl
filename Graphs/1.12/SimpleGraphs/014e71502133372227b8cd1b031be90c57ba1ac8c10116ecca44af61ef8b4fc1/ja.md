```
complete_multipartite_graph(partitions)
```

`sum(partitions)` 頂点を持つ無向 [完全二部グラフ](https://en.wikipedia.org/wiki/Complete_bipartite_graph) を作成します。`0` 頂点のパーティションはスキップされます。

### 実装ノート

パーティションベクトルの eltype を保持します。必要な頂点数が eltype を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> complete_multipartite_graph([1,2,3])
{6, 11} 無向単純 Int64 グラフ

julia> complete_multipartite_graph(Int8[5,5,5])
{15, 75} 無向単純 Int8 グラフ
```
