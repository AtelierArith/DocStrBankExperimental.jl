```
splslda(; kwargs...)
splslda(X, y; kwargs...)
splslda(X, y, weights::Weight; kwargs...)
```

Sparse PLS-LDA.

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments: 

  * `nlv` : Nb. latent variables (LVs) to compute. Must be >= 1.
  * `meth` : Method used for the sparse thresholding.    Possible values are: `:soft`, `:hard`. See thereafter.
  * `nvar` : Nb. variables (`X`-columns) selected for each LV.    Can be a single integer (i.e. same nb. of variables for each LV),    or a vector of length `nlv`.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `scal` : Boolean. If `true`, each column of `X` and Ydummy is scaled by its uncorrected standard deviation   in the PLS computation.

Same as function `plslda` (PLSR-LDA) except that a sparse PLSR (function `splsr`), instead of a PLSR (function `plskern`),  is run on the Y-dummy table. 

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

nlv = 15
meth = :soft
nvar = 10
model = splslda(; nlv, meth, nvar) 
#model = splsqda(; nlv, meth, nvar, alpha = .1) 
#model = splskdeda(; nlv, meth, nvar, a = .9) 
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

embfitm = fitm.fitm.embfitm ; 
@head embfitm.T
@head transf(model, Xtrain)
@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

coef(embfitm)
summary(embfitm, Xtrain)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xtest; nlv = 1:2).pred
```
