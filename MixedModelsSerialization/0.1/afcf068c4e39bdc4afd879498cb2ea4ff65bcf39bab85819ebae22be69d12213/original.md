```
LinearMixedModelSummary{T<:AbstractFloat} <: MixedModelSummary{T}
LinearMixedModelSummary(m::LinearMixedModel)
```

A "summary" of a `LinearMixedModel` with a reduced memory footprint.

This type does not store the model matrices of a `LinearMixedModel` and thus will consume far less memory, especially for models with many observations. Instead, the relevant entities for summarizing a model are stored:

  * fixed effects coefficients and associated variance-covariance matrix
  * random effects covariances
  * the θ vector and `OptSummary` used in optimization
  * (conditional modes and variances are not currently stored)
  * the log likelihood
  * information about the model and residual degrees of freedom

Using these values, it is possible to provide implementations for many but not all methods in `StatsAPI` and `MixedModels`.

!!! warning
    All field names and associated storage format should be considered private implementation details. Use appropriate methods to e.g. extract the log likelihood or the variance-covariance matrix. Stability of the internal structure is **not** guaranteed, even between non-breaking releases.

