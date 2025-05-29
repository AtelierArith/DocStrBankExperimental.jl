```
kdeda(; kwargs...)
kdeda(X, y; kwargs...)
```

Discriminant analysis using non-parametric kernel Gaussian      density estimation (KDE-DA).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).

Keyword arguments:

  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * Keyword arguments of function `dmkern` (bandwidth    definition) can also be specified here.

Same as function `qda` except that class densities are estimated from function `dmkern` instead of function `dmnorm`. 

## Examples

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2")
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
y = dat.X[:, 5]
n = nro(X)
ntest = 30
s = samprand(n, ntest)
Xtrain = X[s.train, :]
ytrain = y[s.train]
Xtest = X[s.test, :]
ytest = y[s.test]
ntrain = n - ntest
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

prior = :unif
#prior = :prop
model = kdeda(; prior)
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

model = kdeda(; prior, a = .5) 
#model = kdeda(; prior, h = .1) 
fit!(model, Xtrain, ytrain)
model.fitm.fitm[1].H
```
