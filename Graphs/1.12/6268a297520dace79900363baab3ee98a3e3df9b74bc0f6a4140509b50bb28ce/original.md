```
attracting_components(g)
```

Return a vector of vectors of integers representing lists of attracting components in the directed graph `g`.

The attracting components are a subset of the strongly connected components in which the components do not have any leaving edges.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0])
{5, 6} directed simple Int64 graph

julia> strongly_connected_components(g)
2-element Vector{Vector{Int64}}:
 [4, 5]
 [1, 2, 3]

julia> attracting_components(g)
1-element Vector{Vector{Int64}}:
 [4, 5]
```
