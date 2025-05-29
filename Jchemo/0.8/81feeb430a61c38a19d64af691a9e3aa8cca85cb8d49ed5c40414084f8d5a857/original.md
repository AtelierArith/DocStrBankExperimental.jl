```
cca(; kwargs...)
cca(X, Y; kwargs...)
cca(X, Y, weights::Weight; kwargs...)
cca!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Canonical correlation Analysis (CCA, RCCA).

  * `X` : First block of data.
  * `Y` : Second block of data.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. Possible values are:   `:none`, `:frob`. See functions `blockscal`.
  * `tau` : Regularization parameter (∊ [0, 1]).
  * `scal` : Boolean. If `true`, each column of blocks `X`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

This function implements a CCA algorithm using SVD decompositions and presented in Weenink 2003 section 2. 

A continuum regularization is available (parameter `tau`). After block centering and scaling,  the function returns block LVs (Tx and Ty) that are proportionnal to the eigenvectors of Projx * Projy  and Projy * Projx, respectively, defined as follows: 

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix
  * Cy = (1 - `tau`) * Y'DY + `tau` * Iy
  * Cxy = X'DY
  * Projx = sqrt(D) * X * invCx * X' * sqrt(D)
  * Projy = sqrt(D) * Y * invCx * Y' * sqrt(D)

where D is the observation (row) metric. Value `tau` = 0 can generate unstability when inverting  the covariance matrices. Often, a better alternative is to use an epsilon value (e.g. `tau` = 1e-8)  to get similar results as with pseudo-inverses.  

After normalized (and using uniform `weights`), the scores returned by the function are expected to be  the same as those returned by functions `rcc` of the R packages `CCA` (González et al.) and `mixOmics`  (Lê Cao et al.) whith their parameters lambda1 and lambda2 set to:

  * lambda1 = lambda2 = `tau` / (1 - `tau`) * n / (n - 1)

See function `plscan` for the details on the `summary` outputs.

## References

González, I., Déjean, S., Martin, P.G.P., Baccini, A., 2008. CCA: An R Package to Extend Canonical Correlation Analysis. Journal of Statistical Software 23, 1-14. https://doi.org/10.18637/jss.v023.i12

Hotelling, H. (1936): “Relations between two sets of variates”, Biometrika 28: pp. 321–377.

Lê Cao, K.-A., Rohart, F., Gonzalez, I., Dejean, S., Abadi, A.J., Gautier, B., Bartolo, F., Monget, P.,  Coquery, J., Yao, F., Liquet, B., 2022. mixOmics: Omics Data Integration Project.  https://doi.org/10.18129/B9.bioc.mixOmics

Weenink, D. 2003. Canonical Correlation Analysis, Institute of Phonetic Sciences, Univ. of Amsterdam,  Proceedings 25, 81-99.

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

nlv = 3
bscal = :frob ; tau = 1e-8
model = cca(; nlv, bscal, tau)
fit!(model, X, Y)
@names model
@names model.fitm

@head model.fitm.Tx
@head transfbl(model, X, Y).Tx

@head model.fitm.Ty
@head transfbl(model, X, Y).Ty

res = summary(model, X, Y) ;
@names res
res.cortx2ty
res.rvx2tx
res.rvy2ty
res.rdx2tx
res.rdy2ty
res.corx2tx 
res.cory2ty 
```
