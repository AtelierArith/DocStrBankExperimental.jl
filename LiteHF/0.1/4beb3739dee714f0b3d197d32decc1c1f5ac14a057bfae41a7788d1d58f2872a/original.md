```
AsimovModel(model::PyHFModel, μ)::PyHFModel
```

Generate the Asimov model when fixing `μ` (POI) to a value. Notice this changes the `priors` and `observed` compare to the original `model`.
