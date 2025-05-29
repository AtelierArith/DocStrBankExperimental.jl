```
ccawold(; kwargs...)
ccawold(X, Y; kwargs...)
ccawold(X, Y, weights::Weight; kwargs...)
ccawold!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Canonical correlation analysis (CCA, RCCA) - Wold Nipals algorithm.

  * `X` : First block of data.
  * `Y` : Second block of data.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. Possible values are:   `:none`, `:frob`. See functions `blockscal`.
  * `tau` : Regularization parameter (∊ [0, 1]).
  * `tol` : Tolerance value for convergence (Nipals).
  * `maxit` : Maximum number of iterations (Nipals).
  * `scal` : Boolean. If `true`, each column of blocks `X`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

This function implements the Nipals ccawold algorithm presented by Tenenhaus 1998 p.204  (related to Wold et al. 1984). 

In this implementation, after each step of LVs computation, X and Y are deflated relatively  to their respective scores (tx and ty). 

A continuum regularization is available (parameter `tau`). After block centering and scaling,  the covariances matrices are computed as follows: 

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix
  * Cy = (1 - `tau`) * Y'DY + `tau` * Iy

where D is the observation (row) metric.  Value `tau` = 0 can generate unstability when inverting the covariance matrices.  Often, a better alternative is to use an epsilon value (e.g. `tau` = 1e-8) to get similar  results as with pseudo-inverses.   

The normed scores returned by the function are expected (using uniform `weights`) to be the  same as those returned by function `rgcca` of the R package `RGCCA`  (Tenenhaus & Guillemot 2017, Tenenhaus et al. 2017). 

See function `plscan` for the details on the `summary` outputs. See function `plscan` for the details on the `summary` outputs.

## References

Tenenhaus, A., Guillemot, V. 2017. RGCCA: Regularized and Sparse Generalized  Canonical Correlation Analysis for Multiblock Data Multiblock data analysis. https://cran.r-project.org/web/packages/RGCCA/index.html 

Tenenhaus, M., 1998. La régression PLS: théorie et pratique. Editions Technip, Paris.

Tenenhaus, M., Tenenhaus, A., Groenen, P.J.F., 2017. Regularized Generalized Canonical  Correlation Analysis: A Framework for Sequential Multiblock Component Methods.  Psychometrika 82, 737–777. https://doi.org/10.1007/s11336-017-9573-x

Wold, S., Ruhe, A., Wold, H., Dunn, III, W.J., 1984. The Collinearity Problem in Linear  Regression. The Partial Least Squares (PLS) Approach to Generalized Inverses.  SIAM Journal on Scientific and Statistical Computing 5, 735–743.  https://doi.org/10.1137/0905052

## Examples

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "linnerud.jld2") 
@load db dat
@names dat
X = dat.X
Y = dat.Y
n, p = size(X)
q = nco(Y)

nlv = 2
bscal = :frob ; tau = 1e-4
model = ccawold(; nlv, bscal, tau, tol = 1e-10)
fit!(model, X, Y)
@names model
@names model.fitm

@head model.fitm.Tx
@head transfbl(model, X, Y).Tx

@head model.fitm.Ty
@head transfbl(model, X, Y).Ty

res = summary(model, X, Y) ;
@names res
res.explvarx
res.explvary
res.cortx2ty
res.rvx2tx
res.rvy2ty
res.rdx2tx
res.rdy2ty
res.corx2tx 
res.cory2ty 
```
