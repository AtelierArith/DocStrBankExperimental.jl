```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::SnowModel,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value for the total energy per unit ground area for the `SnowModel`.

This has already accounted for the area fraction of snow in the definition of S.
