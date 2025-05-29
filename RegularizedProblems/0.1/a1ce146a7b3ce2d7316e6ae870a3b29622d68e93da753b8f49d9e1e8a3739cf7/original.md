```
model = FirstOrderNLSModel(r!, jv!, jtv!; name = "first-order NLS model")
```

A simple subtype of `AbstractNLSModel` to represent a nonlinear least-squares problem with a smooth residual.

## Arguments

  * `r! :: R <: Function`: a function such that `r!(y, x)` stores the residual at `x` in `y`;
  * `jv! :: J <: Function`: a function such that `jv!(u, x, v)` stores the product between the residual Jacobian at `x` and the vector `v` in `u`;
  * `jtv! :: Jt <: Function`: a function such that `jtv!(u, x, v)` stores the product between the transpose of the residual Jacobian at `x` and the vector `v` in `u`;
  * `x :: AbstractVector`: an initial guess.

All keyword arguments are passed through to the `NLPModelMeta` constructor.
