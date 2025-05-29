```
blockdiag(g, h)
```

グラフ `g` にグラフ `h` の頂点と辺を追加して、$|V(g)| + |V(h)|$ の頂点と $|E(g)| + |E(h)|$ の辺を持つグラフを返します。

### 実装ノート

入力グラフの eltype を保持します。生成されたグラフの頂点数が `eltype` を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> blockdiag(g1, g2)
{8, 9} directed simple Int64 graph

julia> foreach(println, edges(blockdiag(g1, g2)))
Edge 1 => 2
Edge 2 => 3
Edge 3 => 1
Edge 3 => 4
Edge 4 => 5
Edge 5 => 4
Edge 6 => 7
Edge 7 => 8
Edge 8 => 6
```
