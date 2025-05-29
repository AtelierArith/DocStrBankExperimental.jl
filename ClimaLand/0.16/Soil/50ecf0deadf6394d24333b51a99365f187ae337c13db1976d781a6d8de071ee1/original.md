```
make_compute_imp_tendency(model::EnergyHydrology)
```

An extension of the function `make_compute_imp_tendency`, for the integrated soil energy and heat equations, including phase change.

This version of this function computes the right hand side of the PDE for `Y.soil.ϑ_l`, which is the only quantity we currently step implicitly.

This has been written so as to work with Differential Equations.jl.
