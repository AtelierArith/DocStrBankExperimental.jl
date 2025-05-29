```
plscan(; kwargs...)
plscan(X, Y; kwargs...)
plscan(X, Y, weights::Weight; kwargs...)
plscan!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Canonical partial least squares regression (Canonical PLS).

  * `X` : First block of data.
  * `Y` : Second block of data.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. Possible values are:   `:none`, `:frob`. See functions `blockscal`.
  * `scal` : Boolean. If `true`, each column of blocks `X`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

Canonical PLS with the Nipals algorithm (Wold 1984, Tenenhaus 1998 chap.11),  referred to as PLS-W2A (i.e. Wold PLS mode A) in Wegelin 2000. The two blocks  `X` and `Y` play a symmetric role.  After each step of scores computation,  X and Y are deflated by the x- and y-scores, respectively. 

Function `summary` returns:

  * `cortx2ty`: Correlations between the X- and Y-LVs.

and for block `X`: 

  * `explvarx` : Proportion of the block inertia (squared Frobenious norm)    explained by the block LVs (`Tx`).
  * `rvx2tx` : RV coefficients between the block and the block LVs.
  * `rdx2tx` : Rd coefficients between the block and the block LVs.
  * `corx2tx` : Correlation between the block variables and the block LVs.

The same is returned for block `Y`.  

## References

Tenenhaus, M., 1998. La régression PLS: théorie et pratique. Editions Technip, Paris.

Wegelin, J.A., 2000. A Survey of Partial Least Squares (PLS) Methods, with Emphasis on  the Two-Block Case (No. 371). University of Washington, Seattle, Washington, USA.

Wold, S., Ruhe, A., Wold, H., Dunn, III, W.J., 1984. The Collinearity Problem in Linear  Regression. The Partial Least Squares (PLS) Approach to Generalized Inverses.  SIAM Journal on Scientific and Statistical Computing 5, 735–743. https://doi.org/10.1137/0905052

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
bscal = :frob
model = plscan(; nlv, bscal)
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
