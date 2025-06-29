```
qda(; kwargs...)
qda(X, y; kwargs...)
qda(X, y, weights::Weight; kwargs...)
```

Quadratic discriminant analysis (QDA, with continuum towards LDA).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `alpha` : Scalar (∈ [0, 1]) defining the continuum between QDA (`alpha = 0`) and LDA (`alpha = 1`).

The low-level method (i.e. having argument `weights`) of the function allows to set any vector of observation weights  to be used in the intermediate computations. In the high-level methods (no argument `weights`), they are automatically  computed from the argument `prior` value: for each class, the total of the observation weights is set equal to  the prior probability corresponding to the class.

**Note:** For highly unbalanced classes, it may be recommended to set 'prior = :unif' when using the function (and to use a score such as `merrp` instead of `errp` when evaluating the perfomance).

For the continuum approach, a value `alpha` > 0 shrinks the class-covariances (Wi) toward a common LDA  covariance ('within-W'). This corresponds to the 'first regularization (Eqs.16)' approach described in  Friedman 1989 (in which the present parameter `alpha` is referred to as 'lambda').

## References

Friedman JH. Regularized Discriminant Analysis. Journal of the American Statistical Association. 1989;  84(405):165-175. doi:10.1080/01621459.1989.10478752.

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

model = qda()
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni
fitm.priors
aggsumv(fitm.weights.w, ytrain)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

## With regularization
model = qda(alpha = .5)
#model = qda(alpha = 1) # = LDA
fit!(model, Xtrain, ytrain)
model.fitm.Wi
res = predict(model, Xtest) ;
errp(res.pred, ytest)
```
