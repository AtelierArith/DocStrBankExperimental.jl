```
fit(MulticlassLDA, nc, X, y; ...)
```

Perform multi-class LDA over a given data set `X` and collecttion of labels `y`.

This function returns the resultant multi-class LDA model as an instance of [`MulticlassLDA`](@ref).

*Parameters*

  * `nc`:  the number of classes
  * `X`:   the matrix of input samples, of size `(d, n)`. Each column in `X` is an observation.
  * `y`:   the vector of class labels, of length `n`. Each element of `y` must be an integer between `1` and `nc`.

**Keyword arguments**

  * `method`: The choice of methods:

      * `:gevd`: based on generalized eigenvalue decomposition (*default*).
      * `:whiten`: first derive a whitening transform from `Sw` and then solve the problem based on eigenvalue

    decomposition of the whiten `Sb`.
  * `outdim`: The output dimension, i.e. dimension of the transformed space `min(d, nc-1)`
  * `regcoef`: The regularization coefficient (*default:* `1.0e-6`). A positive value `regcoef * eigmax(Sw)`   is added to the diagonal of `Sw` to improve numerical stability.
  * `covestimator_between`: Custom covariance estimator for between-class covariance (*default:* `SimpleCovariance()`).   The covariance matrix will be calculated as `cov(covestimator_between, #=data=#; dims=2, mean=zeros(#=...=#))`.   Custom covariance estimators, available in other packages, may result in more robust discriminants for data   with more features than observations.
  * `covestimator_within`:  Custom covariance estimator for within-class covariance (*default:* `SimpleCovariance()`).   The covariance matrix will be calculated as `cov(covestimator_within, #=data=#; dims=2, mean=zeros(nc))`.   Custom covariance estimators, available in other packages, may result in more robust discriminants for data   with more features than observations.

**Notes:**

The resultant projection matrix $P$ satisfies:

$$
\mathbf{P}^T (\mathbf{S}_w + \kappa \mathbf{I}) \mathbf{P} = \mathbf{I}
$$

Here, $\kappa$ equals `regcoef * eigmax(Sw)`. The columns of $P$ are arranged in descending order of the corresponding generalized eigenvalues.

Note that [`MulticlassLDA`](@ref) does not currently support the normalized version using $\mathbf{S}_w^*$ and $\mathbf{S}_b^*$ (see [`SubspaceLDA`](@ref)).
