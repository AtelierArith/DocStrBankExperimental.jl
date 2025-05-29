```
rmsepstand(pred, Y)
```

Compute the standardized square root of the mean of the squared prediction errors      (RMSEP_stand).

  * `pred` : Predictions.
  * `Y` : Observed data.

RMSEP is standardized to `Y`: 

  * RMSEP_stand = RMSEP ./ `Y`.

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
rmsepstand(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
rmsepstand(pred, ytest)
```
