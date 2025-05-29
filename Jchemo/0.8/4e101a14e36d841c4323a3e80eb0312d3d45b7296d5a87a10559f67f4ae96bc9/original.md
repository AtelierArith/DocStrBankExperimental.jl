```
errp(pred, y)
```

Compute the classification error rate (ERRP).

  * `pred` : Predictions.
  * `y` : Observed data (class membership).

## Examples

```julia
using Jchemo

Xtrain = rand(10, 5) 
ytrain = rand(["a" ; "b"], 10)
Xtest = rand(4, 5) 
ytest = rand(["a" ; "b"], 4)

model = plsrda(; nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
errp(pred, ytest)
```
