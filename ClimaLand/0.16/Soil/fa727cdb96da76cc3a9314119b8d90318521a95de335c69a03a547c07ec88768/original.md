```
make_compute_imp_tendency(model::RichardsModel)
```

An extension of the function `make_compute_imp_tendency`, for the Richardson- Richards equation.

This function creates and returns a function which computes the entire right hand side of the PDE for `ϑ_l`, and updates `dY.soil.ϑ_l` in place with that value.
