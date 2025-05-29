```
plskern(; kwargs...)
plskern(X, Y; kwargs...)
plskern(X, Y, weights::Weight; kwargs...)
plskern!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

Partial least squares regression (PLSR) with the "improved kernel algorithm #1"      (Dayal & McGegor, 1997).

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `scal` : Boolean. If `true`, each column of `X` and `Y`    is scaled by its uncorrected standard deviation.

About the row-weighting in PLS algorithms (`weights`): See in particular Schaal et al. 2002, Siccard & Sabatier 2006,  Kim et al. 2011, and Lesnoff et al. 2020. 

## References

Dayal, B.S., MacGregor, J.F., 1997. Improved PLS algorithms.  Journal of Chemometrics 11, 73-85.

Kim, S., Kano, M., Nakagawa, H., Hasebe, S., 2011. Estimation  of active pharmaceutical ingredients content using locally  weighted partial least squares and statistical wavelength  selection. Int. J. Pharm., 421, 269-274.

Lesnoff, M., Metz, M., Roger, J.M., 2020. Comparison of locally  weighted PLS strategies for regression and discrimination on  agronomic NIR Data. Journal of Chemometrics. e3209.  https://onlinelibrary.wiley.com/doi/abs/10.1002/cem.3209

Schaal, S., Atkeson, C., Vijayamakumar, S. 2002. Scalable  techniques from nonparametric statistics for the real time  robot learning. Applied Intell., 17, 49-60.

Sicard, E. Sabatier, R., 2006. Theoretical framework for local  PLS1 regression and application to a rainfall dataset. Comput. Stat.  Data Anal., 51, 1393-1410.

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

nlv = 15
model = plskern(; nlv) ;
#model = plsnipals(; nlv) ;
#model = plswold(; nlv) ;
#model = plsrosa(; nlv) ;
#model = plssimp(; nlv) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f    

res = predict(model, Xtest; nlv = 1:2)
@head res.pred[1]
@head res.pred[2]

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "Nb. LVs", 
    ylabel = "Prop. Explained X-Variance").f
```
