```
lwmlr(; kwargs...)
lwmlr(X, Y; kwargs...)
```

k-Nearest-Neighbours locally weighted multiple linear regression (kNN-LWMLR).

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).

Keyword arguments:

  * `metric` : Type of dissimilarity used to select the neighbors and to compute the weights    (see function `getknn`). Possible values are: `:eucl` (Euclidean), `:mah` (Mahalanobis),    `:sam` (spectral angular distance), `:cor` (correlation distance).
  * `h` : A scalar defining the shape of the weight function computed by function `winvs`. Lower is h,    sharper is the function. See function `winvs` for details (keyword arguments `criw` and `squared` of    `winvs` can also be specified here).
  * `k` : The number of nearest neighbors to select for each observation to predict.
  * `tolw` : For stabilization when very close neighbors.
  * `scal` : Boolean. If `true`, each column of the global `X` is scaled by its uncorrected standard    deviation before the distance and weight computations.
  * `verbose` : Boolean. If `true`, predicting information are printed.

This is the same principle as function `lwplsr` except  that MLR models are fitted on the neighborhoods, instead of  PLSR models.  The neighborhoods are computed directly on `X`  (there is no preliminary dimension reduction).

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

nlv = 20
model0 = pcasvd(; nlv) ;
fit!(model0, Xtrain) 
@head Ttrain = model0.fitm.T 
@head Ttest = transf(model0, Xtest)

metric = :eucl 
h = 2 ; k = 100 
model = lwmlr(; metric, h, k) 
fit!(model, Ttrain, ytrain)
@names model
@names model.fitm
dump(model.fitm.par)

res = predict(model, Ttest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f    

####### Example of fitting the function sinc(x)
####### described in Rosipal & Trejo 2001 p. 105-106 
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
model = lwmlr(metric = :eucl, h = 1.5, k = 20) ;
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "True model")
lines!(ax, x, vec(pred), label = "Fitted model")
axislegend("Method")
f
```
