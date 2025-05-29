```
SoilCanopyModel{FT}(;
    soilco2_type::Type{MM},
    soilco2_args::NamedTuple = (;),
    land_args::NamedTuple = (;),
    soil_model_type::Type{SM},
    soil_args::NamedTuple = (;),
    canopy_component_types::NamedTuple = (;),
    canopy_component_args::NamedTuple = (;),
    canopy_model_args::NamedTuple = (;),
    ) where {
        FT,
        SM <: Soil.EnergyHydrology{FT},
        MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
        }
```

A constructor for the `SoilCanopyModel`, which takes in the concrete model type and required arguments for each component, constructs those models, and constructs the `SoilCanopyModel` from them.

Each component model is constructed with everything it needs to be stepped forward in time, including boundary conditions, source terms, and interaction terms.
