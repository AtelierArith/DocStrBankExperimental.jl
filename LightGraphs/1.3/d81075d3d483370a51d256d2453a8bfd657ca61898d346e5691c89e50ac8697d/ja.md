```
complement(g)
```

グラフの[補グラフ](https://en.wikipedia.org/wiki/Complement_graph)を返します

### 実装ノート

入力グラフの `eltype` を保持します。

# 例

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> foreach(println, edges(complement(g)))
Edge 1 => 3
Edge 1 => 4
Edge 1 => 5
Edge 2 => 1
Edge 2 => 4
Edge 2 => 5
Edge 3 => 2
Edge 3 => 5
Edge 4 => 1
Edge 4 => 2
Edge 4 => 3
Edge 5 => 1
Edge 5 => 2
Edge 5 => 3
```
