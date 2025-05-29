```
make_compute_exp_tendency(model::EnergyHydrology)
```

An extension of the function `make_compute_exp_tendency`, for the integrated soil energy and heat equations, including phase change.

This function creates and returns a function which computes the entire right hand side of the PDE for `Y.soil.ϑ_l, Y.soil.θ_i, Y.soil.ρe_int`, and updates `dY.soil` in place with those values. All of these quantities will be stepped explicitly.

This has been written so as to work with Differential Equations.jl.
