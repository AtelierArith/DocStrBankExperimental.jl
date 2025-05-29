```
MathOptNLPModel(model, hessian=true, name="Generic")
```

Construct a `MathOptNLPModel` from a `JuMP` model.

`hessian` should be set to `false` for multivariate user-defined functions registered without hessian.
