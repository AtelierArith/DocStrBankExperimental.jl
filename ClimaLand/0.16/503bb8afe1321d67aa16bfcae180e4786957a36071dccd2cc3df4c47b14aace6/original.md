```
make_exp_tendency(model::AbstractModel)
```

Returns an `exp_tendency` that updates auxiliary variables and updates the prognostic state of variables that are stepped explicitly.

`compute_exp_tendency!` should be compatible with SciMLBase.jl solvers.
