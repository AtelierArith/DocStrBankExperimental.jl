```
mbplslda(; kwargs...)
mbplslda(Xbl, y; kwargs...)
mbplslda(Xbl, y, weights::Weight; kwargs...)
```

Multiblock PLS-LDA.

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. See function `blockscal`   for possible values.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    and Ydummy is scaled by its uncorrected standard deviation    (before the block scaling) in the MBPLS computation.

The approach is as follows:

1. The training variable `y` (univariate class membership) is transformed to a dummy table (Ydummy)   containing nlev columns, where nlev is the number of classes present in `y`. Each column of   Ydummy is a dummy (0/1) variable.
2. A multivariate MBPLSR (MBPLSR2) is run on {`X`, Ydummy}, returning   a score matrix `T`.
3. A LDA is done on {`T`, `y`}, returning estimates of posterior probabilities  (∊ [0, 1]) of class membership.
4. For a given observation, the final prediction is the class corresponding to the dummy variable for which   the probability estimate is the highest.

The low-level method (i.e. having argument `weights`) of the function allows to set any vector of observation weights  to be used in the intermediate computations. In the high-level methods (no argument `weights`), they are automatically  computed from the argument `prior` value: for each class, the total of the observation weights is set equal to  the prior probability corresponding to the class.

**Note:** For highly unbalanced classes, it may be recommended to set 'prior = :unif' when using the function (and to use a score such as `merrp` instead of `errp` when evaluating the perfomance).

## Examples

```julia
using Jchemo, JLD2, CairoMakie, JchemoData
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
tab(Y.typ)
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(Y.typ, s)
Xtest = X[s, :]
ytest = Y.typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)
wlst = names(X)
wl = parse.(Float64, wlst)
#plotsp(X, wl; nsamp = 20).f
##
listbl = [1:350, 351:700]
Xbltrain = mblock(Xtrain, listbl)
Xbltest = mblock(Xtest, listbl) 

nlv = 15
scal = false
#scal = true
bscal = :none
#bscal = :frob
model = mbplslda(; nlv, bscal, scal)
#model = mbplsqda(; nlv, bscal, alpha = .5, scal)
#model = mbplskdeda(; nlv, bscal, scal)
fit!(model, Xbltrain, ytrain) 
@names model 

@head transf(model, Xbltrain)
@head transf(model, Xbltest)

res = predict(model, Xbltest) ; 
@head res.pred 
@show errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xbltest; nlv = 1:2).pred
```
