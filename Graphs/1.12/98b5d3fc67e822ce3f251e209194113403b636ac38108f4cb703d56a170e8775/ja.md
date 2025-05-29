```
num_self_loops(g)
```

`g`の自己ループの数を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> num_self_loops(g)
0

julia> add_edge!(g, 1, 1);

julia> num_self_loops(g)
1
```
