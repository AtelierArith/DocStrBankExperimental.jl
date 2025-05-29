```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::CanopyModel,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value for the total energy per unit ground area for the `CanopyModel`.

This acts by calling the method for the energy component of the canopy model.
