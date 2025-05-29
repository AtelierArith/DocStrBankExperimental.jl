```
pcanipals(; kwargs...)
pcanipals(X; kwargs...)
pcanipals(X, weights::Weight; kwargs...)
pcanipals!(X::Matrix, weights::Weight; kwargs...)
```

PCA by NIPALS algorithm.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `gs` : Boolean. If `true` (default), a Gram-Schmidt    orthogonalization of the scores and loadings is done   before each X-deflation.
  * `tol` : Tolerance value for stopping    the iterations.
  * `maxit` : Maximum nb. of iterations.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

Let us note D the (n, n) diagonal matrix of weights (`weights.w`) and X the centered matrix in metric D. The function minimizes ||X - T * V'||^2  in metric D  by NIPALS. 

See function `pcasvd` for examples.

## References

Andrecut, M., 2009. Parallel GPU Implementation of Iterative  PCA Algorithms. Journal of Computational Biology 16, 1593-1599.  https://doi.org/10.1089/cmb.2008.0221

K.R. Gabriel, S. Zamir, Lower rank approximation of matrices  by least squares with any choice of weights, Technometrics 21 (1979) 489–498.

Gabriel, R. K., 2002. Le biplot - Outil d'exploration de données  multidimensionnelles. Journal de la Société Française de la Statistique,  143, 5-55.

Lingen, F.J., 2000. Efficient Gram-Schmidt orthonormalisation  on parallel computers. Communications in Numerical Methods in  Engineering 16, 57-66.  https://doi.org/10.1002/(SICI)1099-0887(200001)16:1<57::AID-CNM320>3.0.CO;2-I

Tenenhaus, M., 1998. La régression PLS: théorie et pratique.  Editions Technip, Paris, France.

Wright, K., 2018. Package nipals: Principal Components Analysis  using NIPALS with Gram-Schmidt Orthogonalization.  https://cran.r-project.org/
