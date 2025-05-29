```
project(B::T; layer::Symbol=:bottom, method::Symbol=:simple) where {T<:AbstractMatrix}
```

Project the biadjacency matrix `B` onto one of its layers.

# Arguments

  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`. Layer membership is determined by the bipartite map of the graph.
  * `method`: the method used to compute the adjacency matrix of the projected graph. This can be `:simple` or `:weighted`. Both methods compute    the product of the biadjacency matrix with its transposed, but the `:weighted` method uses the weights of the edges in the projected graph.

# Examples

```jldoctest project_bipartite_matrix
julia> B = [0 0 0 1 1; 0 0 0 1 1; 0 0 0 1 0];

julia> project(B, layer=:bottom)
3×3 Matrix{Bool}:
 0  1  1
 1  0  1
 1  1  0

```

```jldoctest project_bipartite_matrix
julia> project(B, layer=:top)
5×5 Matrix{Bool}:
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  1
 0  0  0  1  0

```

```jldoctest project_bipartite_matrix
julia> B = [0 0 0 1 1; 0 0 0 1 1; 0 0 0 1 0];

julia> project(B, layer=:bottom, method=:weighted)
3×3 Matrix{Int64}:
 0  2  1
 2  0  1
 1  1  0

```

```jldoctest project_bipartite_matrix
julia> project(B, layer=:top, method=:weighted)
5×5 Matrix{Int64}:
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  2
 0  0  0  2  0

```
