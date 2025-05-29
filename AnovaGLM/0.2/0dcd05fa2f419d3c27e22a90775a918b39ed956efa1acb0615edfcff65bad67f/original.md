```
nestedmodels(trm::TableRegressionModel{<: LinearModel}; null::Bool = true, <keyword arguments>)
nestedmodels(trm::TableRegressionModel{<: GeneralizedLinearModel}; null::Bool = true, <keyword arguments>)

nestedmodels(::Type{LinearModel}, formula, data; null::Bool = true, <keyword arguments>)
nestedmodels(::Type{GeneralizedLinearModel}, formula, data, distr::UnivariateDistribution, link::Link = canonicallink(d); null::Bool = true, <keyword arguments>)
```

Generate nested nested models `NestedModels` from a model or formula and data.

The null model will be a model with at least one factor (including intercept) if the link function does not allow factors to be 0 (factors in denominators) or the keyword argument `null` is false (default value is true).

  * `InverseLink` for `Gamma`
  * `InverseSquareLink` for `InverseGaussian`
  * `LinearModel` fitted with `CholeskyPivoted` when `dropcollinear = true`

Otherwise, it will be an empty model.
