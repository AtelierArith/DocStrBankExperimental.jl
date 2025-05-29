```
merge_vertices!(g, vs)
```

`vs`で指定された頂点を単一の頂点に結合します。この新しい頂点のインデックスは`vs`の中で最も低い値になります。`vs`の頂点に接続されているすべてのエッジは、新しく結合された頂点に接続されます。

元の頂点インデックスでインデックス付けされた新しい頂点の値を持つベクトルを返します。

### 実装ノート

[`SimpleGraph`](@ref) のみをサポートします。

# 例

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> collect(edges(g))
4-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
 Edge 4 => 5

julia> merge_vertices!(g, [2, 3])
5-element Vector{Int64}:
 1
 2
 2
 3
 4

julia> collect(edges(g))
3-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
```
