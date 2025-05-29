```
treeda(; kwargs...)
treeda(X, y; kwargs...)
```

Discrimination tree (CART) with DecisionTree.jl.

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).

Keyword arguments:

  * `n_subfeatures` : Nb. variables to select at random    at each split (default: 0 ==> keep all).
  * `max_depth` : Maximum depth of the    decision tree (default: -1 ==> no maximum).
  * `min_sample_leaf` : Minimum number of samples    each leaf needs to have.
  * `min_sample_split` : Minimum number of observations    in needed for a split.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

The function fits a single discrimination tree (CART) using  package `DecisionTree.jl'.

## References

Breiman, L., Friedman, J. H., Olshen, R. A., and  Stone, C. J. Classification And Regression Trees.  Chapman & Hall, 1984.

DecisionTree.jl https://github.com/JuliaAI/DecisionTree.jl

Gey, S., 2002. Bornes de risque, détection de ruptures,  boosting : trois thèmes statistiques autour de CART en régression (These de doctorat). Paris 11.  http://www.theses.fr/2002PA112245

## Examples

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
n, p = size(X) 
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

n_subfeatures = p / 3 
max_depth = 10
model = treeda(; n_subfeatures, max_depth) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
