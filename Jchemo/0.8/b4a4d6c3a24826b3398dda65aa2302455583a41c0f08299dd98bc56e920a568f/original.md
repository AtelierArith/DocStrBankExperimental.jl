```
plstuck(; kwargs...)
plstuck(X, Y; kwargs...)
plstuck(X, Y, weights::Weight; kwargs...)
plstuck!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Tucker's inter-battery method of factor analysis

  * `X` : First block of data.
  * `Y` : Second block of data.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. Possible values are:   `:none`, `:frob`. See functions `blockscal`.
  * `scal` : Boolean. If `true`, each column of blocks `X`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

Inter-battery method of factor analysis (Tucker 1958, Tenenhaus 1998 chap.3). The two blocks  `X` and `X` play a symmetric role.  This method is referred to as PLS-SVD in Wegelin 2000. The method  factorizes the covariance matrix X'Y by SVD. 

See function `plscan` for the details on the `summary` outputs.

## References

Tenenhaus, M., 1998. La régression PLS: théorie et pratique. Editions Technip, Paris.

Tishler, A., Lipovetsky, S., 2000. Modelling and forecasting with robust canonical  analysis: method and application. Computers & Operations Research 27, 217–232.  https://doi.org/10.1016/S0305-0548(99)00014-3

Tucker, L.R., 1958. An inter-battery method of factor analysis. Psychometrika 23, 111–136. https://doi.org/10.1007/BF02289009

Wegelin, J.A., 2000. A Survey of Partial Least Squares (PLS) Methods, with Emphasis  on the Two-Block Case (No. 371). University of Washington, Seattle, Washington, USA.

## Examples

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/linnerud.jld2") 
@load db dat
@names dat
X = dat.X 
Y = dat.Y

model = plstuck(nlv = 3)
fit!(model, X, Y) 
@names model
@names model.fitm

fitm = model.fitm
@head fitm.Tx
@head transfbl(model, X, Y).Tx

@head fitm.Ty
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
