```
fit(AbstractOrdinalMultinomialModel, X, y, link, solver)
```

Fit ordered multinomial model by maximum likelihood estimation.

# Input

  * `y::Vector`: integer vector taking values in `1,...,J`.
  * `X::Matrix`: `n x p` covariate matrix excluding intercept.
  * `link::GLM.Link`: `LogitLink()`, `ProbitLink()`, `CauchitLink()`, or `CloglogLink()`.
  * `solver`: An instance of `Ipopt.Optimizer()` or `NLopt.Optimizer()` (default).

# Output

  * `dd:OrdinalMultinomialModel`: an `OrdinalMultinomialModel` type.
