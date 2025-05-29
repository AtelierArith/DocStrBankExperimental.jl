```
lwplsrda(; kwargs...)
lwplsrda(X, y; kwargs...)
```

kNN-LWPLSR-DA.

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).

Keyword arguments:

  * `nlvdis` : Number of latent variables (LVs) to consider in the global PLS used for the dimension    reduction before computing the dissimilarities. If `nlvdis = 0`, there is no dimension reduction.   If `nlvdis = 0`, there is no dimension reduction.
  * `metric` : Type of dissimilarity used to select the neighbors and to compute the weights    (see function `getknn`). Possible values are: `:eucl` (Euclidean), `:mah` (Mahalanobis),    `:sam` (spectral angular distance), `:cor` (correlation distance).
  * `h` : A scalar defining the shape of the weight function computed by function `winvs`. Lower is h,    sharper is the function. See function `winvs` for details (keyword arguments `criw` and `squared` of    `winvs` can also be specified here).
  * `k` : The number of nearest neighbors to select for each observation to predict.
  * `tolw` : For stabilization when very close neighbors.
  * `nlv` : Nb. latent variables (LVs) for the local (i.e. inside each neighborhood) models.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:unif` (uniform),    `:prop` (proportional).
  * `scal` : Boolean. If `true`, (a) each column of the global `X` (and of the global `Y` if there    is a preliminary PLS reduction dimension) is scaled by its uncorrected standard deviation before to compute    the distances and the weights, and (b) the X and Y scaling is also done within each neighborhood (local level)    for the weighted PLSR.
  * `verbose` : Boolean. If `true`, predicting information are printed.

This is the same principle as function `lwplsr` except that PLSR-DA models, instead of PLSR models, are fitted  on the neighborhoods.

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

nlvdis = 25 ; metric = :mah
h = 2 ; k = 200
nlv = 10
model = lwplsrda(; nlvdis, metric, h, k, nlv) 
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
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
```
