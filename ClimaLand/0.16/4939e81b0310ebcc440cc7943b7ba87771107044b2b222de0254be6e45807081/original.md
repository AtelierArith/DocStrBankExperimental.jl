```
LandSoilBiogeochemistry{FT}(;
    soil_args::NamedTuple = (;),
    biogeochemistry_args::NamedTuple = (;),
) where {FT}
```

A constructor for the `LandSoilBiogeochemistry` model, which takes in the required arguments for each component, constructs those models, and constructs the `LandSoilBiogeochemistry` from them.

Each component model is constructed with everything it needs to be stepped forward in time, including boundary conditions, source terms, and interaction terms.

Additional arguments, like parameters and driving atmospheric data, can be passed in as needed.
