```
AICc(m::BiCM)
```

Compute the corrected Akaike Information Criterion (AICc) for the BiCM model `m`. The parameters of the models most be computed beforehand. 

# Examples

```jldoctest
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> AICc(model)
432.12227535579956

```

See also [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_BiCM_reduced`](@ref MaxEntropyGraphs.L_BiCM_reduced).
