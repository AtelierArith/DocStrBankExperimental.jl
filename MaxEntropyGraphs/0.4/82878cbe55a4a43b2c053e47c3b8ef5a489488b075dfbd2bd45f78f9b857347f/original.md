```
BIC(m::BiCM)
```

Compute the Bayesian Information Criterion (BIC) for the BiCM model `m`. The parameters of the models most be computed beforehand.  BIC is believed to be more restrictive than AIC, as the former favors models with a lower number of parameters than those favored by the latter.

# Examples

```julia-repl
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> BIC(model)
579.3789571131789

```

See also [`AIC`](@ref MaxEntropyGraphs.AIC), [`L_BiCM_reduced`](@ref MaxEntropyGraphs.L_BiCM_reduced).
