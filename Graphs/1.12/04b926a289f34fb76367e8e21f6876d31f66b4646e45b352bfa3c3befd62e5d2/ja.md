```
common_neighbors(g, u, v)
```

グラフ `g` における頂点 `u` と `v` の共通の隣接点を返します。

### 実装ノート

現在のグラフの内部構造への参照を返し、コピーは返しません。結果を変更しないでください。グラフが変更されると、動作は未定義になります：この参照の背後にある配列も変更される可能性がありますが、これは保証されません。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(4);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 4);

julia> add_edge!(g, 4, 1);

julia> add_edge!(g, 1, 3);

julia> common_neighbors(g, 1, 3)
2-element Vector{Int64}:
 2
 4

julia> common_neighbors(g, 1, 4)
1-element Vector{Int64}:
 3
```
