```
turbulent_fluxes_at_a_point(return_extra_fluxes, args...)
```

This is a wrapper function that allows us to dispatch on the type of `return_extra_fluxes` as we compute the turbulent fluxes pointwise. This is needed because space for the extra fluxes is only allocated in the cache when running with a `CoupledAtmosphere`. The function `compute_turbulent_fluxes_at_a_point` does the actual flux computation.

The `return_extra_fluxes` argument indicates whether to return the following:

  * momentum fluxes (`ρτxz`, `ρτyz`)
  * buoyancy flux (`buoy_flux`)
