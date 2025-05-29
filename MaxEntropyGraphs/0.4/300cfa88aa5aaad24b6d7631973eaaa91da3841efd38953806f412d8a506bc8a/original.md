```
V_motifs(B::T, i::Int, j::Int; layer::Symbol=:bottom, skipchecks::Bool=false) where {T<:AbstractMatrix}
```

Count the number of V-motif occurences in the biadjacency matrix `B` between nodes `i` and `j` of a `layer`.

# Arguments

  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`.
  * `skipchecks`: if true, skip the dimension check on `B`

*Notes*: depending on the layer, the tuple (`i`, `j`) denotes rows (:bottom) or columns (:top) of the biadjacency matrix `B`.

# Examples

```jldoctest V_motifs_bipartite_matrix_local
julia> B = [1 1; 1 1; 1 0];

julia> V_motifs(B, 1, 2, layer=:bottom)
2

```

```jldoctest V_motifs_bipartite_matrix_local
julia> V_motifs(B, 1, 2, layer=:top)
2

```
