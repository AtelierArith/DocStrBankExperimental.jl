```
struct SoilCanopyModel{
    FT,
    MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
    SM <: Soil.EnergyHydrology{FT},
    VM <: Canopy.CanopyModel{FT},
} <: AbstractLandModel{FT}
    "The soil microbe model to be used"
    soilco2::MM
    "The soil model to be used"
    soil::SM
    "The canopy model to be used"
    canopy::VM
end
```

A concrete type of land model used for simulating systems with a canopy and a soil component.

  * `soilco2`: The soil microbe model to be used
  * `soil`: The soil model to be used
  * `canopy`: The canopy model to be used
