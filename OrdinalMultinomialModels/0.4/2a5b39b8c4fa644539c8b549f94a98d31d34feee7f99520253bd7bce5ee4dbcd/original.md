```
polr(formula, df, link, solver=NLoptSolver(algorithm=:LD_SLSQP, maxeval=4000))
polr(X, y, link, solver=NLoptSolver(algorithm=:LD_SLSQP, maxeval=4000))
```

Fit ordered multinomial model by maximum likelihood estimation.

# Positional arguments

  * `formula::Formula`: a model formula specifying responses and regressors.
  * `df::DataFrame`: a dataframe. Response variable should take integer values    starting from 1.
  * `y::Vector`: integer vector taking values in `1,...,J`.
  * `X::Matrix`: `n x p` covariate matrix excluding intercept.
  * `link::GLM.Link`: `LogitLink()` (default), `ProbitLink()`, `CauchitLink()`, or `CloglogLink()`.
  * `solver`: An instance of `Ipopt.Optimizer()` or `NLopt.Optimizer()` (default).

# Keyword arguments

  * `wts::AbstractVector=similar(X, 0)`: observation weights.

# Output

  * `dd:PolrModel`: a `PolrModel` type.
