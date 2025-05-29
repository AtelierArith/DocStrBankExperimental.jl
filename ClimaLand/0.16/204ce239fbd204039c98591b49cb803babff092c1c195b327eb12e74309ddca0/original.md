```
LandHydrology{FT}(;
    land_args::NamedTuple = (;),
    soil_model_type::Type{SM},
    soil_args::NamedTuple = (;),
    surface_water_model_type::Type{SW},
    surface_water_args::NamedTuple = (;),
) where {
    FT,
    SM <: Soil.AbstractSoilModel{FT},
    SW <: Pond.AbstractSurfaceWaterModel{FT},
}
```

A constructor for the `LandHydrology` model, which takes in the concrete model type and required arguments for each component, constructs those models, and constructs the `LandHydrology` from them.

Each component model is constructed with everything it needs to be stepped forward in time, including boundary conditions, source terms, and interaction terms.

Additional arguments, like parameters and driving atmospheric data, are passed in as `land_args`.
