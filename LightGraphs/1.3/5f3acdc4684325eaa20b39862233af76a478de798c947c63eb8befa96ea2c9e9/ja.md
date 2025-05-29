```
difference(g, h)
```

グラフ `g` に含まれ、グラフ `h` には含まれないエッジを持つグラフを返します。

### 実装ノート

この関数は、次数が0の頂点を持つグラフを生成する可能性があることに注意してください。入力グラフの `eltype` を保持します。

# 例

```jldoctest
julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> foreach(println, edges(difference(g1, g2)))
Edge 3 => 4
Edge 4 => 5
Edge 5 => 4
```
