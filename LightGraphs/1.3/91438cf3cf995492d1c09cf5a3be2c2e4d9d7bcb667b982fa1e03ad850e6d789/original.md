```
connected_components(g)
```

Return the [connected components](https://en.wikipedia.org/wiki/Connectivity_(graph_theory)) of an undirected graph `g` as a vector of components, with each element a vector of vertices belonging to the component.

For directed graphs, see [`strongly_connected_components`](@ref) and [`weakly_connected_components`](@ref).

# Examples

```jldoctest
julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> connected_components(g)
1-element Array{Array{Int64,1},1}:
 [1, 2, 3]

julia> g = SimpleGraph([0 1 0 0 0; 1 0 1 0 0; 0 1 0 0 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> connected_components(g)
2-element Array{Array{Int64,1},1}:
 [1, 2, 3]
 [4, 5]
```
