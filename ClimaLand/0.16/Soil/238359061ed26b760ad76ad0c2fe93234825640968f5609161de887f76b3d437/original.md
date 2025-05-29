```
make_update_aux(model::EnergyHydrology)
```

An extension of the function `make_update_aux`, for the integrated soil hydrology and energy model.

This function creates and returns a function which updates the auxiliary variables `p.soil.variable` in place.

This has been written so as to work with Differential Equations.jl.
