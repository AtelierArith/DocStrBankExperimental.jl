```
quantile(model::AbstractExtremeValueModel, θ::Vector{<:Real}, p::Real)
```

Compute the quantile of level `p` from the model AbstractExtremeValueModelluated at `θ"".

If the model is non-stationary, then the *effective quantiles* are returned, *i.e.* one for each covariate value.
