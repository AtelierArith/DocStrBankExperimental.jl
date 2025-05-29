```
V_motifs(A::T; layer::Symbol=:bottom, skipchecks::Bool=false) where {T<:AbstractMatrix}
```

Count the total number of V-motif occurence in the biadjacency matrix `A` for one of its layers.

# Arguments

  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`. Layer membership is determined by the bipartite map of the graph.
  * `skipchecks`: if true, skip the dimension check on `A`

# Examples

```jldoctest V_motifs_bipartite_matrix
julia> A = [1 1; 1 1; 1 0];

julia> V_motifs(A, layer=:bottom)
4

```

```jldoctest V_motifs_bipartite_matrix
julia> V_motifs(A, layer=:top)
2

```
