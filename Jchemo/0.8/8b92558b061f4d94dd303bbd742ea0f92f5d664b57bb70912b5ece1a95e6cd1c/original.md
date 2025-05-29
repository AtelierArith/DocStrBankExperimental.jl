```
plsrout(; kwargs...)
plsrout(X, Y; kwargs...)
plsrout(X, Y, weights::Weight; kwargs...)
pcaout!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Robust PLSR using outlierness.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of latent variables (LVs).
  * `prm` : Proportion of the data removed (hard rejection of outliers)    for each outlierness measure.
  * `scal` : Boolean. If `true`, each column of `X` is scaled by its MAD    when computing the outlierness and by its uncorrected standard    deviation when computing weighted PCA.

Robust PLSR combining outlyingness measures and weighted PLSR (WPLSR). This is the same principle as function `pcaout` (see the help page) but the final step is a weighted PLSR instead of a weighted PCA.  

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)

nlv = 15
model = plsrout(; nlv)
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f    

res = predict(model, Xtest; nlv = 1:2)
@head res.pred[1]
@head res.pred[2]
```
