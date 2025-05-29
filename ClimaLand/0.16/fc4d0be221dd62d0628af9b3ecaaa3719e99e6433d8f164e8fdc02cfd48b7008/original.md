```
struct LandHydrology{
    FT,
    SM <: Soil.AbstractSoilModel{FT},
    SW <: Pond.AbstractSurfaceWaterModel{FT},
} <: AbstractLandModel{FT}
```

A concrete type of land model used for simulating systems with a soil and surface water component.

  * `soil`: The soil model
  * `surface_water`: The surface water model
