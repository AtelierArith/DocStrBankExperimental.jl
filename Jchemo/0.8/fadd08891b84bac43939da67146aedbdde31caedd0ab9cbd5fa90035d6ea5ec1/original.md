```
rasvd(; kwargs...)
rasvd(X, Y; kwargs...)
rasvd(X, Y, weights::Weight; kwargs...)
rasvd!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Redundancy analysis (RA), a.k.a PCA on instrumental variables (PCAIV)

  * `X` : First block of data.
  * `Y` : Second block of data.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. Possible values are:   `:none`, `:frob`. See functions `blockscal`.
  * `tau` : Regularization parameter (∊ [0, 1]).
  * `scal` : Boolean. If `true`, each column of blocks `X`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

See e.g. Bougeard et al. 2011a,b and Legendre & Legendre 2012. Let Y*hat be the fitted values  of the regression of `Y` on `X`. The scores `Ty` are the PCA scores of Y*hat. The scores `Tx` are  the fitted values of the regression of `Ty` on `X`.

A continuum regularization is available.  After block centering and scaling, the covariances  matrices are computed as follows: 

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix

where D is the observation (row) metric. Value `tau` = 0 can generate unstability when  inverting the covariance matrices. A better alternative is generally to use an epsilon value  (e.g. `tau` = 1e-8) to get similar results as with pseudo-inverses.  

## References

Bougeard, S., Qannari, E.M., Lupo, C., Chauvin, C., 2011-a. Multiblock redundancy analysis from a user's  perspective. Application in veterinary epidemiology. Electronic Journal of Applied Statistical Analysis  4, 203-214. https://doi.org/10.1285/i20705948v4n2p203

Bougeard, S., Qannari, E.M., Rose, N., 2011-b. Multiblock redundancy analysis: interpretation tools  and application in epidemiology. Journal of Chemometrics 25, 467-475.  https://doi.org/10.1002/cem.1392

Legendre, V., Legendre, L., 2012. Numerical Ecology. Elsevier, Amsterdam, The Netherlands.

Tenenhaus, A., Guillemot, V. 2017. RGCCA: Regularized and Sparse Generalized Canonical Correlation  Analysis for Multiblock Data Multiblock data analysis.  https://cran.r-project.org/web/packages/RGCCA/index.html 

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
model = rasvd(; nlv, bscal, tau)
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
