```
make_update_boundary_fluxes(
    land::LandHydrology{FT, SM, SW},
) where {FT, SM <: Soil.RichardsModel{FT}, SW <: Pond.PondModel{FT}}
```

A method which makes a function; the returned function updates the auxiliary variable `p.soil_infiltration`, which is needed for both the boundary condition for the soil model and the source term (runoff) for the surface water model.

This function is called each ode function evaluation.
