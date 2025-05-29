```
knnda(; kwargs...)
knnda(X, y; kwargs...)
```

k-Nearest-Neighbours weighted discrimination (kNN-DA).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).

Keyword arguments:

  * `metric` : Type of dissimilarity used to select the neighbors and to compute the weights    (see function `getknn`). Possible values are: `:eucl` (Euclidean), `:mah` (Mahalanobis),    `:sam` (spectral angular distance), `:cor` (correlation distance).
  * `h` : A scalar defining the shape of the weight function computed by function `winvs`. Lower is h,    sharper is the function. See function `winvs` for details (keyword arguments `criw` and `squared` of    `winvs` can also be specified here).
  * `k` : The number of nearest neighbors to select for each observation to predict.
  * `tolw` : For stabilization when very close neighbors.
  * `scal` : Boolean. If `true`, each column of the global `X` is scaled by its uncorrected standard    deviation before the distance and weight computations.

This function has the same principle as function `knnr` except that a discrimination replaces the  regression. A weighted vote is done over the neighborhood, and the prediction corresponds to the most  frequent class.

## Examples

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
n = nro(X) 
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(Y.typ, s)
Xtest = X[s, :]
ytest = Y.typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

metric = :eucl
h = 2 ; k = 10
model = knnda(; metric, h, k) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show errp(res.pred, ytest)
conf(res.pred, ytest).cnt

## With dimension reduction
model1 = pcasvd(; nlv = 15)
metric = :mah ; h = 1 ; k = 3 
model2 = knnda(; metric, h, k) 
model = pip(model1, model2)
fit!(model, Xtrain, ytrain)
@head pred = predict(model, Xtest).pred 
errp(pred, ytest)
```
