```
make_explicit_tendency(model::Soil.RichardsModel)
```

An extension of the function `make_compute_imp_tendency`, for the Richardson- Richards equation.

Construct the tendency computation function for the explicit terms of the RHS, which are horizontal components and source/sink terms.
