```
model = FirstOrderModel(f, ∇f!; name = "first-order model")
```

A simple subtype of `AbstractNLPModel` to represent a smooth objective.

## Arguments

  * `f :: F <: Function`: a function such that `f(x)` returns the objective value at `x`;
  * `∇f! :: G <: Function`: a function such that `∇f!(g, x)` stores the gradient of the objective at `x` in `g`;
  * `x :: AbstractVector`: an initial guess.

All keyword arguments are passed through to the `NLPModelMeta` constructor.
