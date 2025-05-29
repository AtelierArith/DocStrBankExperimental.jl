```
ClimaLand.total_liq_water_vol_per_area!(
    surface_field,
    model::EnergyHydrology,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value for the total liquid water volume per unit ground area for the `EnergyHydrology`.

The water in all phases is accounted for by converting ice volume to liquid water volume using the ratio of the density of ice to the density of water.
