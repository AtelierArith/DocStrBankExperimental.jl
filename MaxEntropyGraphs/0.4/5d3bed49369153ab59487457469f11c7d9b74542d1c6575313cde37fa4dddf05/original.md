```
BIC(m::UBCM)
```

Compute the Bayesian Information Criterion (BIC) for the UBCM model `m`. The parameters of the models most be computed beforehand.  BIC is believed to be more restrictive than AIC, as the former favors models with a lower number of parameters than those favored by the latter.

# Examples

```julia-repl
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> BIC(model)
552.5770135138283

```

See also [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_UBCM_reduced`](@ref MaxEntropyGraphs.L_UBCM_reduced).
