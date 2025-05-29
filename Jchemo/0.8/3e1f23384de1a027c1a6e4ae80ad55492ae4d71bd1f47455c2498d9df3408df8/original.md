```
pcanipalsmiss(; kwargs...)
pcanipals(X; kwargs...)
pcanipals(X, weights::Weight; kwargs...)
pcanipals!(X::Matrix, weights::Weight; kwargs...)
```

PCA by NIPALS algorithm allowing missing data.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `gs` : Boolean. If `true` (default), a Gram-Schmidt    orthogonalization of the scores and loadings is done   before each X-deflation.
  * `tol` : Tolerance value for stopping    the iterations.
  * `maxit` : Maximum nb. of iterations.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

## References

Wright, K., 2018. Package nipals: Principal Components Analysis  using NIPALS with Gram-Schmidt Orthogonalization.  https://cran.r-project.org/

## Examples

```julia
X = [1 2. missing 4 ; 4 missing 6 7 ; 
    missing 5 6 13 ; missing 18 7 6 ; 
    12 missing 28 7] 

nlv = 3 
tol = 1e-15
scal = false
#scal = true
gs = false
#gs = true
model = pcanipalsmiss(; nlv, tol, gs, maxit = 500, scal)
fit!(model, X)
@names model 
@names model.fitm
fitm = model.fitm ;
fitm.niter
fitm.sv
fitm.V
fitm.T
## Orthogonality 
## only if gs = true
fitm.T' * fitm.T
fitm.V' * fitm.V

## Impute missing data in X
model = pcanipalsmiss(; nlv = 2, gs = true) ;
fit!(model, X)
Xfit = xfit(model.fitm)
s = ismissing.(X)
X_imp = copy(X)
X_imp[s] .= Xfit[s]
X_imp
```
