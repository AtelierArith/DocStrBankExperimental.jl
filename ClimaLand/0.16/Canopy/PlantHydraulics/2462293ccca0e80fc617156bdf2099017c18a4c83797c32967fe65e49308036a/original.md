```
ClimaLand.total_liq_water_vol_per_area!(
    surface_field,
    model::PlantHydraulicsModel,
    Y,
    p,
    t,
```

)

A function which updates `surface_field` in place with the value of the plant hydraulic models total water volume.

Note that this is general for any number of canopy layers, but it assumes that the LAI and SAI given are per layer. This is distinct from the BigLeaf approach, in which the LAI and SAI refer to the integrated area index with heigh.
