```
V_motifs(m::BiCM, i::Int, j::Int; layer::Symbol=:bottom, precomputed::Bool=false)
```

Count the number of expected V-motif occurences in the BiCM `m` between nodes `i` and `j` of a `layer`.

# Arguments

  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`.
  * `precomputed`: if true, the expected values of the biadjacency matrix are used, otherwise the parameters are computed from the model parameters.

*Notes*: depending on the layer, the tuple (`i`, `j`) denotes rows (:bottom) or columns (:top) of the expected biadjacency matrix `A`.

# Examples

```jldoctest V_motifs_bicm_local
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> V_motifs(model, 16, 13, layer=:bottom), V_motifs(model, 16, 13, layer=:bottom, precomputed=false)
(3.385652998856112, 3.3856529988561115)

```

```jldoctest V_motifs_bicm_local
julia> V_motifs(model, 5, 1, layer=:top), V_motifs(model, 5, 1, layer=:top, precomputed=false)
(9.46988024296453, 9.469880242964528)

```
