```
mbplsr(; kwargs...)
mbplsr(Xbl, Y; kwargs...)
mbplsr(Xbl, Y, weights::Weight; kwargs...)
mbplsr!(Xbl::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

Multiblock PLSR (MBPLSR).

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. global latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. See function `blockscal`   for possible values.
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    and `Y` is scaled by its uncorrected standard deviation    (before the block scaling).

This function runs a PLSR on {X, `Y`} where X is the horizontal  concatenation of the blocks in `Xbl`. The function gives the  same global LVs and predictions as function `mbplswest`, but is much faster.

Function `summary` returns: 

  * `explvarx` : Proportion of the total X inertia (squared Frobenious norm)    explained by the global LVs.
  * `rvxbl2t` : RV coefficients between each block and the global LVs.
  * `rdxbl2t` : Rd coefficients between each block (= Xbl[k]) and the global LVs.
  * `corx2t` : Correlation between the X-variables and the global LVs.

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
ytrain = y[s]
Xbltest = mblock(rmrow(X, s), listbl)
ytest = rmrow(y, s) 
ntrain = nro(ytrain) 
ntest = nro(ytest) 
ntot = ntrain + ntest 
(ntot = ntot, ntrain , ntest)

nlv = 3
bscal = :frob
model = mbplsr(; nlv, bscal)
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

## This MBPLSR can also be implemented with function pip

model1 = blockscal(; bscal, centr = true) ;
model2 = mbconcat()
model3 = plskern(; nlv, scal = false) ;
model = pip(model1, model2, model3)
fit!(model, Xbltrain, ytrain)
@head T =  model.model[3].fitm.T  # = transf(model, Xbltrain)
transf(model, Xbltest)
predict(model, Xbltest).pred 
```
