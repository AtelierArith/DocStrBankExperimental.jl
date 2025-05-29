```
has_self_loops(g)
```

Return true if `g` has any self loops.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> has_self_loops(g)
false

julia> add_edge!(g, 1, 1);

julia> has_self_loops(g)
true
```
