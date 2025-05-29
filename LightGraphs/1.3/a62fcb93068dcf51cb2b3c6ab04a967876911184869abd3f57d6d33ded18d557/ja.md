```
has_self_loops(g)
```

`g` に自己ループがある場合は true を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> has_self_loops(g)
false

julia> add_edge!(g, 1, 1);

julia> has_self_loops(g)
true
```
