```
is_bipartite(g)
```

グラフ `g` が [二部グラフ](https://en.wikipedia.org/wiki/Bipartite_graph) であれば `true` を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> is_bipartite(g)
true

julia> add_edge!(g, 1, 3);

julia> is_bipartite(g)
false
```
