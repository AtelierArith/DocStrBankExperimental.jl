```
make_compute_exp_tendency(model::SoilCO2Model)
```

An extension of the function `make_compute_exp_tendency`, for the soilco2 equation. This function creates and returns a function which computes the entire right hand side of the PDE for `C`, and updates `dY.soil.C` in place with that value. These quantities will be stepped explicitly.

This has been written so as to work with Differential Equations.jl.
