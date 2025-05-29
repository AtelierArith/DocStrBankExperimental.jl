```
zero(G)
```

Return a zero-vertex, zero-edge version of the graph type `G`. The fallback is defined for graph values `zero(g::G) = zero(G)`.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> zero(typeof(g))
{0, 0} directed simple Int64 graph

julia> zero(g)
{0, 0} directed simple Int64 graph
```
