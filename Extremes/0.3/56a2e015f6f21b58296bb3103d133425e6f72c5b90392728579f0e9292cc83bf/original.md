```
quantile(model::EVA, θ::Vector{<:Real}, p::Real)
```

Compute the quantile of level `p` from the model evaluated at `θ"".

If the model is non-stationary, then the *effective quantiles* are returned, *i.e.* one for each covariate value.
