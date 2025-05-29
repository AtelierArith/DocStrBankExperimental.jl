```
ClimaLand.source!(dY::ClimaCore.Fields.FieldVector,
                 src::RootExtraction,
                 Y::ClimaCore.Fields.FieldVector,
                 p::NamedTuple
                 model::EnergyHydrology)
```

An extension of the `ClimaLand.source!` function,  which computes source terms for the soil model; this method returns the water and energy loss/gain due to root extraction.
