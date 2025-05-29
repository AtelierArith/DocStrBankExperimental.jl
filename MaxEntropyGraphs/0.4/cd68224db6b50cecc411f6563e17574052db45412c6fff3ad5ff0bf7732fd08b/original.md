```
V_motifs(m::BiCM; layer::Symbol=:bottom)
```

Count the total number of V-motif occurences in the BiCM `m` for one of its layers.

# Arguments

  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`. Layer membership is determined by the bipartite map of the graph.
  * `precomputed`: if true, the expected values of the biadjacency matrix are used, otherwise the parameters are computed from the model parameters.

# Examples

```jldoctest V_motifs_bicm
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> V_motifs(model, layer=:bottom), V_motifs(model, layer=:bottom, precomputed=false)
(449.2569925909879, 449.2569925909879)

```

```jldoctest V_motifs_bicm
julia> V_motifs(model, layer=:top), V_motifs(model, layer=:top, precomputed=false)
(180.2569926636081, 180.2569926636081)
```
