```
faem(S, mean, n; ...)
```

Performs factor analysis using an expectation-maximization algorithm for a given sample covariance matrix `S`[^2].

**Parameters**

  * `S`: The sample covariance matrix.
  * `mean`: The mean vector of original samples, which can be a vector of length $d$,

or an empty vector indicating a zero mean.

  * `n`: The number of observations.

Returns the resultant [`FactorAnalysis`](@ref) model.

**Note:** This function accepts two keyword arguments: `maxoutdim`,`tol`, and `maxiter`.
