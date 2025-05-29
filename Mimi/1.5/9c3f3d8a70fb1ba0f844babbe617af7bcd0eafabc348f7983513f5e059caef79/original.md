```
create_marginal_model(base::Model, delta::Float64=1.0)
```

Create a `MarginalModel` where `base` is the baseline model and `delta` is the difference used to create the `marginal` model.  Return the resulting `MarginaModel` which shares the internal `ModelDef` between the `base` and `marginal`.
