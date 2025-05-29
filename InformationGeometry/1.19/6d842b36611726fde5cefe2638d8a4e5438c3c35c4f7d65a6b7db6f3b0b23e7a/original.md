```
EmbedModelVia(model, F::Function; Domain::HyperCube=FullDomain(GetArgLength(F),Inf)) -> Union{Function,ModelMap}
```

Transforms a model function via `newmodel(x, θ) = oldmodel(x, F(θ))`. A `Domain` for the new model can optionally be specified for `ModelMap`s.
