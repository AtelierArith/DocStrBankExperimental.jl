```
curve_fit(model, xdata, ydata, p0) -> fit
curve_fit(model, xdata, ydata, wt, p0) -> fit
```

Fit data to a non-linear `model`. `p0` is an initial model parameter guess (see Example), and `wt` is an optional array of weights. The return object is a composite type (`LsqFitResult`), with some interesting values:

  * `fit.resid` : residuals = vector of residuals
  * `fit.jacobian` : estimated Jacobian at solution

additionally, it is possible to query the degrees of freedom with

  * `dof(fit)`
  * `coef(fit)`

## Example

```julia
# a two-parameter exponential model
# x: array of independent variables
# p: array of model parameters
model(x, p) = p[1]*exp.(-x.*p[2])

# some example data
# xdata: independent variables
# ydata: dependent variable
xdata = range(0, stop=10, length=20)
ydata = model(xdata, [1.0 2.0]) + 0.01*randn(length(xdata))
p0 = [0.5, 0.5]

fit = curve_fit(model, xdata, ydata, p0)
```
