```
make_compute_exp_tendency(model::AbstractModel)
```

Return a `compute_exp_tendency!` function that updates state variables that we will be stepped explicitly. This fallback sets all tendencies of this model to zero, which is appropriate for models that do not have any explicit tendencies to update. Note that we cannot set `dY .= 0` here because this would overwrite the tendencies of all models in the case of an integrated LSM.

`compute_exp_tendency!` should be compatible with SciMLBase.jl solvers.
