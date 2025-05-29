```
join(g, h)
```

グラフ `g` と `h` を `blockdiag` を使用して結合し、次に `g` の頂点と `h` の頂点の間のすべてのエッジを追加したグラフを返します。

### 実装ノート

入力グラフの eltype を保持します。生成されたグラフの頂点数が eltype を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g = join(star_graph(3), path_graph(2))
{5, 9} undirected simple Int64 graph

julia> collect(edges(g))
9-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 1 => 5
 Edge 2 => 4
 Edge 2 => 5
 Edge 3 => 4
 Edge 3 => 5
 Edge 4 => 5
```
