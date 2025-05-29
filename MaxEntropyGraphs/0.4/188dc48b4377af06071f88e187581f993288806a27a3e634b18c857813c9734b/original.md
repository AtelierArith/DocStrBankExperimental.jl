```
AICc(m::DBCM)
```

Compute the corrected Akaike Information Criterion (AICc) for the DBCM model `m`. The parameters of the models most be computed beforehand. 

# Examples

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> AICc(model)
314.5217467272881

```

See also [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_DBCM_reduced`](@ref MaxEntropyGraphs.L_DBCM_reduced).
