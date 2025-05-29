```
make_update_boundary_fluxes(
    land::SoilSnowModel{FT, SnM, SoM},
) where {
    FT,
    SnM <: Snow.SnowModel{FT},
    SoM <: Soil.EnergyHydrology{FT},
    }
```

A method which makes a function; the returned function updates the additional auxiliary variables for the integrated model, as well as updates the boundary auxiliary variables for all component models.

This function is called each ode function evaluation, prior to the tendency function evaluation.

In this method, we

1. Compute the ground heat flux between soil and snow. This is required to update the snow and soil boundary fluxes
2. Update the snow boundary fluxes, which also computes any excess flux of energy or water which occurs when the snow

completely melts in a step. In this case, that excess must go to the soil for conservation

3. Update the soil boundary fluxes use precomputed ground heat flux and excess fluxes from snow.
4. Compute the net flux for the atmosphere, which is useful for assessing conservation.
