```
ClimaLand.total_liq_water_vol_per_area!(
    surface_field,
    model::SnowModel,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value for the total liquid water volume per unit ground area for the `SnowModel`.

This has already accounted for the area fraction of snow in the definition of S; it also accounts for both liquid and frozen water present in the snow, as the snow water equivalent is already the total liquid water volume present in the snow if all the snow melted, per unit ground area.
