```
intersect(g, h)
```

グラフ `g` とグラフ `h` の両方にのみ存在するエッジを持つグラフを返します。

### 実装ノート

この関数は、次数が0の頂点を持つグラフを生成する可能性があります。入力グラフのeltypeを保持します。

# 例

```jldoctest
julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> foreach(println, edges(intersect(g1, g2)))
Edge 1 => 2
Edge 2 => 3
Edge 3 => 1
```
