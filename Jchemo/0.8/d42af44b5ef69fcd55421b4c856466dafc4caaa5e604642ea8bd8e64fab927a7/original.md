```
rpd(pred, Y)
```

Compute the ratio "deviation to model performance" (RPD).

  * `pred` : Predictions.
  * `Y` : Observed data.

This is the ratio of the deviation to the model performance  to the deviation, defined by:

  * RPD = Std(Y) / RMSEP

where Std(Y) is the standard deviation. 

Since Std(Y) = RMSEP(null model) where the null model is  the simple average, this also gives:

  * RPD = RMSEP(null model) / RMSEP

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
rpd(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
rpd(pred, ytest)
```
