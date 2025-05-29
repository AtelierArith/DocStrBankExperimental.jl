```
n_components(V::Vector{T}, D::Dict{Tuple{T, T}, Bool})
```

Outputs an array representing the connected components of the graph given by the vertices V and the edges D (more precisely, the edges are given by the keys of D whose entries are "true").

# Example

julia> V = [1, 2, 3, 4];

julia> D = Dict{Tuple{Int, Int}, Bool}((1, 2) => true, (3, 4) => true, (2, 3) => false);

julia> components(V, D) 2-element Vector{Vector{Int64}}:  [1, 2]  [3, 4] ```
