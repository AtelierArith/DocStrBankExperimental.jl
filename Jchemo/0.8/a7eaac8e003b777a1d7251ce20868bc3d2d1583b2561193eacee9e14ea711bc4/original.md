```
mbplswest(; kwargs...)
mbplswest(Xbl, Y; kwargs...)
mbplswest(Xbl, Y, weights::Weight; kwargs...)
mbplswest!(Xbl::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Multiblock PLSR (MBPLSR) - Nipals algorithm.

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. global latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. See function `blockscal`   for possible values.
  * `tol` : Tolerance value for convergence (Nipals).
  * `maxit` : Maximum number of iterations (Nipals).
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

This functions implements the MBPLSR Nipals algorithm such  as in Westerhuis et al. 1998. The function gives the same  global scores and predictions as function `mbplsr`.

Function `summary` returns: 

  * `explvarx` : Proportion of the total X inertia (squared Frobenious norm)    explained by the global LVs.
  * `rvxbl2t` : RV coefficients between each block and the global LVs.
  * `rdxbl2t` : Rd coefficients between each block (= Xbl[k]) and the global LVs.
  * `cortbl2t` : Correlations between the block LVs (= Tbl[k]) and the global LVs.
  * `corx2t` : Correlation between the X-variables and the global LVs.

## References

Westerhuis, J.A., Kourti, T., MacGregor, J.F., 1998. Analysis  of multiblock and hierarchical PCA and PLS models. Journal of  Chemometrics 12, 301–321.  https://doi.org/10.1002/(SICI)1099-128X(199809/10)12:5<301::AID-CEM515>3.0.CO;2-S

## Examples

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "ham.jld2") 
@load db dat
@names dat 
X = dat.X
Y = dat.Y
y = Y.c1
group = dat.group
listbl = [1:11, 12:19, 20:25]
s = 1:6
Xbltrain = mblock(X[s, :], listbl)
Xbltest = mblock(rmrow(X, s), listbl)
ytrain = y[s]
ytest = rmrow(y, s) 
ntrain = nro(ytrain) 
ntest = nro(ytest) 
ntot = ntrain + ntest 
(ntot = ntot, ntrain , ntest)

nlv = 3
bscal = :frob
scal = false
#scal = true
model = mbplswest(; nlv, bscal, scal)
fit!(model, Xbltrain, ytrain)
@names model 
@names model.fitm
@head model.fitm.T
@head transf(model, Xbltrain)
transf(model, Xbltest)

res = predict(model, Xbltest)
res.pred 
rmsep(res.pred, ytest)

res = summary(model, Xbltrain) ;
@names res 
res.explvarx
res.rvxbl2t
res.rdxbl2t
res.cortbl2t
res.corx2t 
```
