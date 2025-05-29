```
partial_fitted(model::MixedModel,
               fe::AbstractVector{<:AbstractString},
               re::Dict{Symbol}=Dict(fn => fe for fn in fnames(model));
               mode=:include,
               type=:linpred)
```

Compute "partial" fitted values.

Partial fitted values are useful for computing partial residuals. They are the fitted values obtained by setting selected model terms to zero, while preserving the other values at their original estimates.

The fixed effects coefficients to use (`fe`) are specified as vector of strings. For specifying no coefficients, use the empty string vector `String[]`.

The random effects `re` are specified as a dictionary, with the grouping variables as keys and the vector of group-level coefficients specified as vectors. For example, `Dict(:subj => ["(Intercept)"])` specifies that `(1|subj)` should be kept. The default is to match the specified fixed effects for all grouping variables, but note that this will fail when the fixed effects specification is incompatible with any grouping variable.

The keyword argument `mode` specifies whether the fixed and random effects specifications are treated as coefficients to `:include` or `:exclude`.

For `GeneralizedLinearMixedModel`, the keyword argument `type` specifies whether the predictions should be returned on the scale of linear predictor (`:linpred`) or on the response scale (`:response`).

!!! warning
    Partial fitted values can be misleading for generalized linear mixed models on the response scale because of the nonlinear nature of the link function. For example, in logistic regression the partial fitted values are computed on the linear predictor scale, i.e. the log odds scale, and then transformed to the response scale, i.e. the probablitiy scale. However, a simple additive contribution on the log odds scale is not additive on the probability scale. More directly, it is impossible to decompose the effects of individual predictors into simple additive contributions on the original scale.


!!! note
    For both the fixed and the random effects, the relevant entities are the coefficient names, not the original term names.


!!! warning
    The intercept is **not** automatically / implicitly included and must always be explicitly specified.


!!! warning
    This functionality has not been tested on and thus verified to work with models with rank-deficient fixed effects.


This functionality is similar to the [remef](https://github.com/hohenstein/remef) package in R.
