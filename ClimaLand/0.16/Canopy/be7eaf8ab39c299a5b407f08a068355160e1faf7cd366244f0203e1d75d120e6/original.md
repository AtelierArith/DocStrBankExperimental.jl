```
ClimaLand.total_liq_water_vol_per_area!(
    surface_field,
    model::CanopyModel,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value for the total liquid water volume per unit ground area for the `CanopyModel`.

This acts by calling the method for the PlantHydraulics component of the canopy model.
