```
make_imp_tendency(model::AbstractImExModel)
```

Returns an `imp_tendency` that updates auxiliary variables and updates the prognostic state of variables that are stepped implicitly.

`compute_imp_tendency!` should be compatible with SciMLBase.jl solvers.
