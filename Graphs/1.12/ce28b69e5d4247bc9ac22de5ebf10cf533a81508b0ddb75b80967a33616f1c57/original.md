```
weakly_connected_components(g)
```

Return the weakly connected components of the graph `g`. This is equivalent to the connected components of the undirected equivalent of `g`. For undirected graphs this is equivalent to the [`connected_components`](@ref) of `g`.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> weakly_connected_components(g)
1-element Vector{Vector{Int64}}:
 [1, 2, 3]
```
