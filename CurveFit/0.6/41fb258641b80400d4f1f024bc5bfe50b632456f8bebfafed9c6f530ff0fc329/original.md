#Uses the object created by `curve_fit` to estimate values

The `call` method is overloaded so that the fit object can  be used as a function:

## Example:

x = 1.0:10.0 @. y = 2*x + 1 + randn()

fit = curve_fit(LinearFit, x, y)

y1 = fit(5.1) y2 = apply_fit(fit, 5.1)
