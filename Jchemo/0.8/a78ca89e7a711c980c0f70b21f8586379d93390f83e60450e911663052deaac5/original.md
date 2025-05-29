```
soplsr(; kwargs...)
soplsr(Xbl, Y; kwargs...)
soplsr(Xbl, Y, weights::Weight; kwargs...)
soplsr!(Xbl::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Multiblock sequentially orthogonalized PLSR (SO-PLSR).

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    and `Y` is scaled by its uncorrected standard deviation.

## References

Biancolillo et al. , 2015. Combining SO-PLS and linear  discriminant analysis for multi-block classification.  Chemometrics and Intelligent Laboratory Systems, 141, 58-67.

Biancolillo, A. 2016. Method development in the area of  multi-block analysis focused on food analysis. PhD.  University of copenhagen.

Menichelli et al., 2014. SO-PLS as an exploratory tool for path modelling. Food Quality and Preference, 36, 122-134.

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

nlv = 2
#nlv = [2, 1, 2]
#nlv = [2, 0, 1]
scal = false
#scal = true
model = soplsr(; nlv, scal)
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
