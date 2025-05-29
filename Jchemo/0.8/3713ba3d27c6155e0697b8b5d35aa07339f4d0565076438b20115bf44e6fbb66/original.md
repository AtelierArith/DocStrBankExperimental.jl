```
r2(pred, Y)
```

Compute the R2 coefficient.

  * `pred` : Predictions.
  * `Y` : Observed data.

The rate R2 is calculated by:

  * R2 = 1 - MSEP(current model) / MSEP(null model)

where the "null model" is the overall mean.  For predictions over CV or test sets, and/or for  non linear models, it can be different from the square  of the correlation coefficient (`cor2`) between the true  data and the predictions. 

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
r2(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
r2(pred, ytest)
```
