```
reverse(g)
```

元の有向グラフからすべてのエッジが逆転した有向グラフを返します。

### 実装ノート

入力グラフのeltypeを保持します。

# 例

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> foreach(println, edges(reverse(g)))
Edge 1 => 3
Edge 2 => 1
Edge 3 => 2
Edge 4 => 3
Edge 4 => 5
Edge 5 => 4
```
