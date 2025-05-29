```
OxygenGasExchangeBoundaryCondition(FT = Float64; 
                                   transfer_velocity = SchmidtScaledTransferVelocity(schmidt_number = OxygenPolynomialSchmidtNumber(FT)),
                                   water_concentration = OxygenConcentration(),
                                   air_concentration = 9352.7, # mmolO₂/m³
                                   wind_speed = 2,
                                   kwagrs...)
```

Returns a `FluxBoundaryCondition` for the gas exchange between oxygen dissolved in the water specified by the the `OxygenConcentration` in the base model, and `air_concentration` with `transfer_velocity` (see `GasExchangeBoundaryCondition` for details).

`kwargs` are passed on to `GasExchangeBoundaryCondition`.
