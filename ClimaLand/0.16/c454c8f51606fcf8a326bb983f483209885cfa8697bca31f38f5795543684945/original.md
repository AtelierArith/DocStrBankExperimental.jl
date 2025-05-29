```
struct LandSoilBiogeochemistry{
    FT,
    SEH <: Soil.EnergyHydrology{FT},
    SB <: Soil.Biogeochemistry.SoilCO2Model{FT},
} <: AbstractLandModel{FT}
```

A concrete type of land model used for simulating systems with a soil energy, hydrology, and biogeochemistry component.

  * `soil`: The soil model
  * `soilco2`: The biochemistry model
