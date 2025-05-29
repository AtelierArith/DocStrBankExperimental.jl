```
mlr(; kwargs...)
mlr(X, Y; kwargs...)
mlr(X, Y, weights::Weight; kwargs...)
mlr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

Compute a mutiple linear regression model (MLR) by using the QR algorithm.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `noint` : Boolean. Define if the model is computed    with an intercept or not.

Safe but can be little slower than other methods.

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 2:4]
y = dat.X[:, 1]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
Xtrain = X[s.train, :]
ytrain = y[s.train]
Xtest = X[s.test, :]
ytest = y[s.test]

model = mlr()
#model = mlrchol()
#model = mlrpinv()
#model = mlrpinvn() 
fit!(model, Xtrain, ytrain) 
@names model
@names model.fitm
fitm = model.fitm ;
fitm.B
fitm.int 
coef(model) 
res = predict(model, Xtest)
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f    

model = mlr(noint = true)
fit!(model, Xtrain, ytrain) 
coef(model) 

model = mlrvec()
fit!(model, Xtrain[:, 1], ytrain) 
coef(model) 
```
