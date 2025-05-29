```
neighbors(g, v)
```

頂点 `v` から到達可能なすべての隣接点のリストを返します。有向グラフの場合、デフォルトは [`outneighbors`](@ref) と同等です。入出力の隣接点をリストするには [`all_neighbors`](@ref) を使用してください。

### 実装ノート

現在のグラフの内部構造への参照を返し、コピーは返しません。結果を変更しないでください。グラフが変更されると、動作は未定義になります。この参照の背後にある配列も変更される可能性がありますが、それは保証されません。

# 例

```jldoctest
julia> using LightGraphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> neighbors(g, 1)
0-element Array{Int64,1}

julia> neighbors(g, 2)
1-element Array{Int64,1}:
 3

julia> neighbors(g, 3)
1-element Array{Int64,1}:
 1
```
