```
vertex_cover(g, DegreeVertexCover())
```

貪欲ヒューリスティックを使用して頂点被覆を取得します。

### 実装ノート

辺は、少なくとも1つの端点が頂点被覆に含まれている場合に被覆されていると言います。頂点被覆を空の集合で初期化し、未被覆の辺が最も多い頂点を反復的に選択します。

### パフォーマンス

実行時間: O((|V|+|E|)*log(|V|)) メモリ: O(|V|)

# 例

```jldoctest
julia> using Graphs

julia> vertex_cover(path_graph(3), DegreeVertexCover())
1-element Vector{Int64}:
 2

julia> vertex_cover(cycle_graph(3), DegreeVertexCover())
2-element Vector{Int64}:
 1
 3
```
