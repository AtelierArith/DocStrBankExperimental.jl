```
BIC(m::DBCM)
```

Compute the Bayesian Information Criterion (BIC) for the DBCM model `m`. The parameters of the models most be computed beforehand.  BIC is believed to be more restrictive than AIC, as the former favors models with a lower number of parameters than those favored by the latter.

# Examples

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> BIC(model)
415.69929372350714

```

See also [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_DBCM_reduced`](@ref MaxEntropyGraphs.L_DBCM_reduced).
