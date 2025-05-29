```
treer(; kwargs...)
treer(X, y; kwargs...)
```

Regression tree (CART) with DecisionTree.jl.

  * `X` : X-data (n, p).
  * `y` : Univariate y-data (n).

Keyword arguments:

  * `n_subfeatures` : Nb. variables to select at random    at each split (default: 0 ==> keep all).
  * `max_depth` : Maximum depth of the    decision tree (default: -1 ==> no maximum).
  * `min_sample_leaf` : Minimum number of samples    each leaf needs to have.
  * `min_sample_split` : Minimum number of observations    in needed for a split.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

The function fits a single regression tree (CART) using  package `DecisionTree.jl'.

## References

Breiman, L., Friedman, J. H., Olshen, R. A., and  Stone, C. J. Classification And Regression Trees.  Chapman & Hall, 1984.

DecisionTree.jl https://github.com/JuliaAI/DecisionTree.jl

Gey, S., 2002. Bornes de risque, détection de ruptures,  boosting : trois thèmes statistiques autour de CART en régression (These de doctorat). Paris 11.  http://www.theses.fr/2002PA112245

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
p = nco(X)

n_subfeatures = p / 3 
max_depth = 15
model = treer(; n_subfeatures, max_depth) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    
```
