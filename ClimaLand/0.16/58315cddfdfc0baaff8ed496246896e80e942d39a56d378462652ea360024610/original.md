```
boundary_vars(::AbstractBC , ::ClimaLand.TopBoundary)
```

The list of symbols for additional variables to add to the model auxiliary state, for models solving PDEs, which defaults  to adding storage for the top boundary flux fields, but which can be extended depending on the type of  boundary condition used.

For the Soil and SoilCO2 models - which solve PDEs - the  tendency functions and  update*boundary*fluxes functions are coded to access the field  `:top_bc`  to be present in the model cache, which is why  this is the default.  If this is not your (PDE) model's  desired behavior, you can extend this function with a new method.

The field `top_bc_wvec` is created to prevent allocations only; it is used in the tendency function only.

Use this function in the exact same way you would use `auxiliary_vars`.
