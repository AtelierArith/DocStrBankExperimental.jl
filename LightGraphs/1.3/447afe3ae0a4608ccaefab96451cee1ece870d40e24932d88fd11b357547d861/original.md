```
num_self_loops(g)
```

Return the number of self loops in `g`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> num_self_loops(g)
0

julia> add_edge!(g, 1, 1);

julia> num_self_loops(g)
1
```
