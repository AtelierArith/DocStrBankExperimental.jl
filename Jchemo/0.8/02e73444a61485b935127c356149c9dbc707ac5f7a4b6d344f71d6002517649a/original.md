```
dkplslda(; kwargs...)
dkplslda(X, y; kwargs...)
dkplslda(X, y, weights::Weight; kwargs...)
```

DKPLS-LDA.

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute. Must be >= 1.
  * `kern` : Type of kernel used to compute the Gram matrices. Possible values are: `:krbf`, `:kpol`. See respective    functions `krbf` and `kpol` for their keyword arguments.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `scal` : Boolean. If `true`, each column of `X` is scaled by its uncorrected standard deviation.

Same as function `plslda` (PLS-LDA) except that a direct kernel PLSR (function `dkplsr`), instead of a PLSR  (function `plskern`), is run on the Y-dummy table. 

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
gamma = .1
model = dkplslda(; nlv, gamma) 
#model = dkplslda(; nlv, gamma, prior = :unif) 
#model = dkplsqda(; nlv, gamma, alpha = .5) 
#model = dkplskdeda(; nlv, gamma, a = .5) 
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

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xtest; nlv = 1:2).pred
```
