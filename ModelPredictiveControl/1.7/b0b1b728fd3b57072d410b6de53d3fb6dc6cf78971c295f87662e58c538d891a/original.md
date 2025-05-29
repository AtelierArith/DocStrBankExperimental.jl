```
LinModel(model::NonLinModel; x=model.x0+model.xop, u=model.uop, d=model.dop)
```

Call [`linearize(model; x, u, d)`](@ref) and return the resulting linear model.
