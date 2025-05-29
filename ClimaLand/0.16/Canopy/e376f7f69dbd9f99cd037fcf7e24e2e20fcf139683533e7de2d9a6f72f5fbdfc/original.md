```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::BigLeafEnergyModel,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value of the big leaf model's energy.

Note that this assumes that there is at most a single canopy and stem  component, and that the area index for them refers to the integrated area index (in height) - not the value per layer.
