```
SimpleGraphFromIterator(iter)
```

Create a [`SimpleGraph`](@ref) from an iterator `iter`. The elements in iter must be of `type <: SimpleEdge`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> h = SimpleGraphFromIterator(edges(g));

julia> collect(edges(h))
2-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
```
