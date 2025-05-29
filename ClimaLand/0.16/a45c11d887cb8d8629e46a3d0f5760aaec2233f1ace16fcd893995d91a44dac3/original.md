```
struct SoilSnowModel{
    FT,
    SnM <: Snow.SnowModel{FT},
    SoM <: Soil.EnergyHydrology{FT},
} <: AbstractLandModel{FT}
    "The snow model to be used"
    snow::SnM
    "The soil model to be used"
    soil::SoM
end
```

A concrete type of land model used for simulating systems with snow and soil (and eventually rivers).

  * `snow`: The snow model to be used
  * `soil`: The soil model to be used
