```
mae(pred, Y)
```

Compute the median absolute error (MAE).

  * `pred` : Predictions.
  * `Y` : Observed data.

## Examples

```julia
using Jchemo 

Xtrain = rand(10, 5) 
Ytrain = rand(10, 2)
ytrain = Ytrain[:, 1]
Xtest = rand(4, 5) 
Ytest = rand(4, 2)
ytest = Ytest[:, 1]

model = plskern(nlv = 2)
fit!(model, Xtrain, Ytrain)
pred = predict(model, Xtest).pred
mae(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
mae(pred, ytest)
```
