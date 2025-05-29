```
make_update_boundary_fluxes(
    land::LandModel{FT, MM, SM, RM, SnM},
) where {
    FT,
    MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
    SM <: Soil.RichardsModel{FT},
    RM <: Canopy.CanopyModel{FT}
    SnM <: Snow.SnowModel{FT}
    }
```

A method which makes a function; the returned function updates the additional auxiliary variables for the integrated model, as well as updates the boundary auxiliary variables for all component models.

This function is called each ode function evaluation, prior to the tendency function evaluation.
