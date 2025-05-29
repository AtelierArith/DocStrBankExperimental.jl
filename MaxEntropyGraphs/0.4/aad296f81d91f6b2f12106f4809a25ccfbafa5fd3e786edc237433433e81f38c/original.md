```
AIC(m::BiCM)
```

Compute the Akaike Information Criterion (AIC) for the BiCM model `m`. The parameters of the models most be computed beforehand.  If the number of empirical observations becomes too small with respect to the number of parameters, you will get a warning. In  that case, the corrected AIC (AICc) should be used instead.

# Examples

```julia
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> AIC(model);
[...]

```

See also [`AICc`](@ref MaxEntropyGraphs.AICc), [`L_BiCM_reduced`](@ref MaxEntropyGraphs.L_BiCM_reduced).
