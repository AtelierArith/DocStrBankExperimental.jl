```
AICc(m::UBCM)
```

Compute the corrected Akaike Information Criterion (AICc) for the UBCM model `m`. The parameters of the models most be computed beforehand. 

# Examples

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> AICc(model)
409.891217554954

```

See also [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_UBCM_reduced`](@ref MaxEntropyGraphs.L_UBCM_reduced).
