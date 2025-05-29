```
prune(b::GaussianMixture, T::Real, U::Real, J_max::Integer)
```

Prune the posterior Gaussian-Mixture next PHD state

Arguments:

  * `b::GaussianMixture` Posterior state distribution. [Gaussian Mixture]
  * `T::Real` Truncation threshold.  Drop distributions with weight less than T
  * `U::Real` Merging threshold.  Merge if (μ*1-μ*2)^T * Σ^-1 * (μ*1-μ*2) < U
  * `J_max::Integer` Maximum number of features
