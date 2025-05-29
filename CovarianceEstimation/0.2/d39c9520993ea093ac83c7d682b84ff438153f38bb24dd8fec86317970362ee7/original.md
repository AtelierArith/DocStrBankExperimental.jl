```
LinearShrinkage(target, shrinkage; corrected=false, drop_var0=false)
```

Linear shrinkage estimator described by equation $(1 - \lambda) S + \lambda F$ where $S$ is standard covariance matrix, $F$ is shrinkage target described by argument `target` and $\lambda$ is a shrinkage parameter, either given explicitly in `shrinkage` or automatically determined according to one of the supported methods.

The corrected estimator is used if `corrected` is true. `drop_var0=true` drops the zero-variance variables from the computation of `\lambda`.
