```
rosaplsr(; kwargs...)
rosaplsr(Xbl, Y; kwargs...)
rosaplsr(Xbl, Y, weights::Weight; kwargs...)
rosaplsr!(Xbl::Vector, Y::Matrix, weights::Weight; kwargs...)
```

Multiblock ROSA PLSR (Liland et al. 2016).

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

The function has the following differences with the original algorithm  of Liland et al. (2016):

  * Scores T (latent variables LVs) are not normed to 1.
  * Multivariate `Y` is allowed. In such a case, the squared residuals are    summed over the columns to find the winning block for each global LV    (therefore, Y-columns should have the same scale).

## References

Liland, K.H., Næs, T., Indahl, U.G., 2016. ROSA — a fast  extension of partial least squares regression for multiblock  data analysis. Journal of Chemometrics 30, 651–662.  https://doi.org/10.1002/cem.2824

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
scal = false
#scal = true
model = rosaplsr(; nlv, scal)
fit!(model, Xbltrain, ytrain)
@names model 
@names model.fitm
@head model.fitm.T
@head transf(model, Xbltrain)
transf(model, Xbltest)

res = predict(model, Xbltest)
res.pred 
rmsep(res.pred, ytest)
```
