```
bayespca(S, mean, n; ...)
```

Compute probabilistic PCA using a Bayesian algorithm for a given sample covariance matrix `S`.

*Parameters*:

  * `S`: The sample covariance matrix.
  * `mean`: The mean vector of original samples, which can be a vector of length `d`,

or an empty vector indicating a zero mean.

  * `n`: The number of observations.

Returns the resultant [`PPCA`](@ref) model.

**Notes:**

  * This function accepts three keyword arguments: `maxoutdim`, `tol`, and `maxiter`.
  * Function uses the `maxoutdim` parameter as an upper boundary when it automatically

determines the latent space dimensionality.
