```
rr(; kwargs...)
rr(X, Y; kwargs...)
rr(X, Y, weights::Weight; kwargs...)
rr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

Ridge regression (RR) implemented by SVD factorization.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `lb` : Ridge regularization parameter "lambda".
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

## References

Cule, E., De Iorio, M., 2012. A semi-automatic method  to guide the choice of ridge parameter in ridge regression.  arXiv:1205.0686.

Hastie, T., Tibshirani, R., 2004. Efficient quadratic  regularization for expression arrays. Biostatistics 5, 329-340.  https://doi.org/10.1093/biostatistics/kxh010

Hastie, T., Tibshirani, R., Friedman, J., 2009. The  elements of statistical learning: data mining,  inference, and prediction, 2nd ed. Springer, New York.

Hoerl, A.E., Kennard, R.W., 1970. Ridge Regression: Biased  Estimation for Nonorthogonal Problems. Technometrics 12, 55-67.  https://doi.org/10.1080/00401706.1970.10488634

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

lb = 1e-3
model = rr(; lb) 
#model = rrchol(; lb) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

coef(model)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    

## !! Only for function 'rr' (not for 'rrchol')
coef(model; lb = 1e-1)
res = predict(model, Xtest; lb = [.1 ; .01])
@head res.pred[1]
@head res.pred[2]
```
