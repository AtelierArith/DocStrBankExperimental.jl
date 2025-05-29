```
make_compute_imp_tendency(model::AbstractModel)
```

Return a `compute_imp_tendency!` function that updates state variables that we will be stepped implicitly. This fallback sets all tendencies of this model to zero, which is appropriate for models that do not have any implicit tendencies to update. Note that we cannot set `dY .= 0` here because this would overwrite the tendencies of all models in the case of an integrated LSM.

`compute_imp_tendency!` should be compatible with SciMLBase.jl solvers.
