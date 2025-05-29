```
mlrda(; kwargs...)
mlrda(X, y; kwargs...)
mlrda(X, y, weights::Weight)
```

Discrimination based on multple linear regression (MLR-DA).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).

The approach is as follows:

1. The training variable `y` (univariate class membership) is transformed to a dummy table (Ydummy)   containing nlev columns, where nlev is the number of classes present in `y`. Each column of   Ydummy is a dummy (0/1) variable.
2. Then, a multiple linear regression (MLR) is run on {`X`, Ydummy}, returning predictions of the dummy variables   (= object `posterior` returned by fuction `predict`).  These predictions can be considered as unbounded   estimates (i.e. eventually outside of [0, 1]) of the class membership probabilities.
3. For a given observation, the final prediction is the class corresponding to the dummy variable for which   the probability estimate is the highest.

The low-level method (i.e. having argument `weights`) of the function allows to set any vector of observation weights  to be used in the intermediate computations. In the high-level methods (no argument `weights`), they are automatically  computed from the argument `prior` value: for each class, the total of the observation weights is set equal to  the prior probability corresponding to the class.

**Note:** For highly unbalanced classes, it may be recommended to set 'prior = :unif' when using the function (and to use a score such as `merrp` instead of `errp` when evaluating the perfomance).

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

model = mlrda()
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
```
