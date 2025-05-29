```
sep(pred, Y)
```

Compute the corrected SEP ("SEP_c"), i.e. the standard deviation of      the prediction errors.

  * `pred` : Predictions.
  * `Y` : Observed data.

## References

Bellon-Maurel, V., Fernandez-Ahumada, E., Palagos, B.,  Roger, J.-M., McBratney, A., 2010. Critical review of  chemometric indicators commonly used for assessing the  quality of the prediction of soil attributes by NIR  spectroscopy. TrAC Trends in Analytical Chemistry 29,  1073–1081.  https://doi.org/10.1016/j.trac.2010.05.006

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
sep(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
sep(pred, ytest)
```
