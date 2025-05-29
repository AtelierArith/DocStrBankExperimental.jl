```
pip(args...)
```

Build a pipeline of models.

  * `args...` : Succesive models, see examples.

## Examples

```julia
using JLD2, CairoMakie, JchemoData
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "cassav.jld2") 
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
ntrain = nro(Xtrain)
ntest = nro(Xtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)

## Pipeline Snv :> Savgol :> Pls :> Svmr

model1 = snv()
model2 = savgol(npoint = 11, deriv = 2, degree = 3)
model3 = plskern(nlv = 15)
model4 = svmr(gamma = 1e3, cost = 1000, epsilon = .1)
model = pip(model1, model2, model3, model4)
fit!(model, Xtrain, ytrain)
res = predict(model, Xtest) ; 
@head res.pred 
rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",
      ylabel = "Observed").f
```
