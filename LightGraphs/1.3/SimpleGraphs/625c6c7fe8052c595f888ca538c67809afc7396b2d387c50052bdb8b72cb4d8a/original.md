```
SimpleDiGraphFromIterator(iter)
```

Create a `SimpleDiGraph` from an iterator `iter`. The elements in `iter` must be of `type <: SimpleEdge`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleDiGraph(2);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 1);

julia> h = SimpleDiGraphFromIterator(edges(g))
{2, 2} directed simple Int64 graph

julia> collect(edges(h))
2-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 1
```
