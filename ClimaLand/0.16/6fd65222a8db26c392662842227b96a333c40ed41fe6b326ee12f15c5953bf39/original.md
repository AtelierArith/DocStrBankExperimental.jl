```
SoilSnowModel{FT}(;
    land_args::NamedTuple = (;),
    snow_model_type::Type{SnM},
    snow_args::NamedTuple = (;),
    soil_model_type::Type{SoM},
    soil_args::NamedTuple = (;),
    ) where {
        FT,
        SnM <: Snow.SnowModel{FT},
        SoM <: Soil.EnergyHydrology{FT},
        }
```

A constructor for the `LandHydrology`, which takes in the concrete model type and required arguments for each component, constructs those models, and constructs the `SoilSnowModel` from them.

Each component model is constructed with everything it needs to be stepped forward in time, including boundary conditions, source terms, and interaction terms.
