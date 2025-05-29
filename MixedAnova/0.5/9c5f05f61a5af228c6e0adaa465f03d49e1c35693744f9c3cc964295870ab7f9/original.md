```
nestedmodels(trm::TableRegressionModel{<: LinearModel}; null::Bool = false, <keyword arguments>)
nestedmodels(trm::TableRegressionModel{<: GeneralizedLinearModel}; null::Bool = false, <keyword arguments>)
nestedmodels(model::LinearMixedModel; null::Bool = false, <keyword arguments>)

nestedmodels(::Type{LinearModel}, formula, data; null::Bool = true, <keyword arguments>)
nestedmodels(::Type{GeneralizedLinearModel}, formula, data, distr::UnivariateDistribution, link::Link = canonicallink(d); null::Bool = true, <keyword arguments>)
nestedmodels(::Type{LinearMixedModel}, f::FormulaTerm, tbl; null::Bool = true, wts = [], contrasts = Dict{Symbol, Any}(), verbose::Bool = false, REML::Bool = false)
```

Generate nested models from a model or formula and data.

The null model will be a model with at least one factor (including intercept) if the link function does not allow factors to be 0 (factors in denominators).

  * `InverseLink` for `Gamma`
  * `InverseSquareLink` for `InverseGaussian`
  * `LinearModel` fitted with `CholeskyPivoted` when `dropcollinear = true`

Otherwise, it will be an empty model.
