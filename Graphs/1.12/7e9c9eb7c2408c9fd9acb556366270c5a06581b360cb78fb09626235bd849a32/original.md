```
strongly_connected_components_tarjan(g)
```

Compute the strongly connected components of a directed graph `g` using Tarjan's algorithm.

Return an array of arrays, each of which is the entire connected component.

### Implementation Notes

The returned components will be ordered reverse topologically.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> strongly_connected_components_tarjan(g)
2-element Vector{Vector{Int64}}:
 [3]
 [1, 2]

julia> g = SimpleDiGraph(11)
{11, 0} directed simple Int64 graph

julia> edge_list=[(1,2),(2,3),(3,4),(4,1),(3,5),(5,6),(6,7),(7,5),(5,8),(8,9),(9,8),(10,11),(11,10)];

julia> g = SimpleDiGraph(Edge.(edge_list))
{11, 13} directed simple Int64 graph

julia> strongly_connected_components_tarjan(g)
4-element Vector{Vector{Int64}}:
 [8, 9]
 [5, 6, 7]
 [1, 2, 3, 4]
 [10, 11]
```
