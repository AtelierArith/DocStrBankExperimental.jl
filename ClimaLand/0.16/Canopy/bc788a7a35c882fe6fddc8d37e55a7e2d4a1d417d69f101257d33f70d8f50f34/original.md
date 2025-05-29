```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::AbstractCanopyEnergyModel,
    Y,
    p,
    t,
```

)

A default function which errors for generic energy models for the canopy.

Note that we only support two models for canopy energy. The `BigLeafEnergyModel` has a special method for this, and the other has the temperature prescribed and does not conserve energy.
