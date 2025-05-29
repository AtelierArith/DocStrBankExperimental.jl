```
CarbonDioxideGasExchangeBoundaryCondition(FT = Float64; 
                                          carbon_chemistry = CarbonChemistry(FT),
                                          transfer_velocity = SchmidtScaledTransferVelocity(schmidt_number = CarbonDioxidePolynomialSchmidtNumber(FT)),
                                          air_concentration = 413, # ppmv
                                          wind_speed = 2,
                                          water_concentration = nothing,
                                          silicate_and_phosphate_names = nothing,
                                          kwargs...)
```

Returns a `FluxBoundaryCondition` for the gas exchange between carbon dioxide dissolved in the water specified by the `carbon_chemisty` model, and `air_concentration` with `transfer_velocity` (see  `GasExchangeBoundaryCondition` for details).

`silicate_and_phosphate_names` should either be `nothing`, a `Tuple``of symbols specifying the name of the silicate and phosphate tracers, or a`NamedTuple`of values for the`carbon_chemistry` model.

`kwargs` are passed on to `GasExchangeBoundaryCondition`.

Note: The model always requires `T`, `S`, `DIC`, and `Alk` to be present in the model.
