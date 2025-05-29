```
add_edge!(g, e)
```

Add an edge `e` to graph `g`. Return `true` if edge was added successfully, otherwise return `false`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2)
true

julia> add_edge!(g, 2, 3)
false
```
