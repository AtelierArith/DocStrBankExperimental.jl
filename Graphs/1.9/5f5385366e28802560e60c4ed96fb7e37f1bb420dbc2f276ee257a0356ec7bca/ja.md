```
outneighbors(g, v)
```

頂点 `v` に出ている辺で接続されているすべての隣接点のリストを返します。

# 実装ノート

現在のグラフの内部構造への参照を返し、コピーは返しません。結果を変更しないでください。グラフが変更されると、動作は未定義になります：この参照の背後にある配列も変更される可能性がありますが、これは保証されません。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> outneighbors(g, 4)
1-element Vector{Int64}:
 5
```
