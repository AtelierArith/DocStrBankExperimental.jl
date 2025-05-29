```
posterior(fx::FiniteGP{<:PosteriorGP}, y::AbstractVector{<:Real})
```

Construct the posterior distribution over `fx.f` when `f` is itself a `PosteriorGP` by updating the Cholesky factorisation of the covariance matrix and avoiding recomputing it from the original covariance matrix. It does this by using `update_chol` functionality.

Other aspects are similar to a regular posterior.
