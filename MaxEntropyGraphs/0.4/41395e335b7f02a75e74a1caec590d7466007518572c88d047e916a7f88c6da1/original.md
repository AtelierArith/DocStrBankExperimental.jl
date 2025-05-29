```
AIC(m::DBCM)
```

Compute the Akaike Information Criterion (AIC) for the DBCM model `m`. The parameters of the models most be computed beforehand.  If the number of empirical observations becomes too small with respect to the number of parameters, you will get a warning. In  that case, the corrected AIC (AICc) should be used instead.

# Examples

```julia-repl
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> AIC(model);
┌ Warning: The number of observations is small with respect to the number of parameters (n/k < 40). Consider using the corrected AIC (AICc) instead.
[...]

```

See also [`AICc`](@ref MaxEntropyGraphs.AICc), [`L_DBCM_reduced`](@ref MaxEntropyGraphs.L_DBCM_reduced).
