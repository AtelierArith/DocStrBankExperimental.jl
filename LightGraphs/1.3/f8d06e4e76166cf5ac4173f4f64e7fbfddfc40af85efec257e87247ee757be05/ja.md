負の重みサイクルがグラフに存在する場合にtrueを返す関数。

# 例

```jldoctest
julia> g = complete_graph(3);

julia> d = [1 -3 1; -3 1 1; 1 1 1];

julia> has_negative_edge_cycle_spfa(g, d)
true

julia> g = complete_graph(4);

julia> d = [1 1 -1 1; 1 1 -1 1; 1 1 1 1; 1 1 1 1];

julia> has_negative_edge_cycle_spfa(g, d);
false
```
