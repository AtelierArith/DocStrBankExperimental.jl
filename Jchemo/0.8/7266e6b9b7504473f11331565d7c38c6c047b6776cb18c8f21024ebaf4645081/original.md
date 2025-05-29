```
merrp(pred, y)
```

Compute the mean intra-class classification error rate.

  * `pred` : Predictions.
  * `y` : Observed data (class membership).

ERRP (see function `errp`) is computed for each class. Function `merrp` returns the average of these intra-class ERRPs.   

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
merrp(pred, ytest)
```
