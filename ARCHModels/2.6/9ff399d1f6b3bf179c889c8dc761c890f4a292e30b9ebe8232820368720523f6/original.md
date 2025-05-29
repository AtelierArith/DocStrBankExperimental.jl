```
selectmodel(::Type{<:ARMA}, data; kwargs...)  -> UnivariateARCHModel
```

Fit a number of `ARMA{p, q}` models to `data` and return that which minimizes the [BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion).

# Keyword arguments:

  * `dist=StdNormal`: the error distribution.
  * `minlags=1`: minimum lag length to try in each parameter of `VS`.
  * `maxlags=3`: maximum lag length to try in each parameter of `VS`.
  * `criterion=bic`: function that takes a `UnivariateARCHModel` and returns the criterion to minimize.
  * `show_trace=false`: print `criterion` to screen for each estimated model.
  * `algorithm=BFGS(), autodiff=:forward, kwargs...`: passed on to the optimizer.
