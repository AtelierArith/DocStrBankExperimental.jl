```
pcr(; kwargs...)
pcr(X, Y; kwargs...)
pcr(X, Y, weights::Weight; kwargs...)
pcr!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Principal component regression (PCR) with a SVD factorization.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * Same as function `pcasvd`

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
model = pcr(; nlv) ;
fit!(model, Xtrain, ytrain)
@names model
fitm = model.fitm ;
@names fitm
@names fitm.fitm

@head fitm.fitm.T
@head transf(model, X)

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

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "Nb. LVs", ylabel = "Prop. Explained X-Variance").f
```
