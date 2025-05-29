```
residcla(pred, y)
```

Compute the discrimination residual vector (0 = no error, 1 = error).

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
residcla(pred, ytest)
```
