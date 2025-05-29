```
informationmatrix(model::StatisticalModel; expected::Bool = true)
```

Return the information matrix of the model. By default the Fisher information matrix is returned, while the observed information matrix can be requested with `expected = false`.
