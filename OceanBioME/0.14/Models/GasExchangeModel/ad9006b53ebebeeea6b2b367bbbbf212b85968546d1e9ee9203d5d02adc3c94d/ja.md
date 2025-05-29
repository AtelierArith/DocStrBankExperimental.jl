```
OxygenGasExchangeBoundaryCondition(FT = Float64; 
                                   transfer_velocity = SchmidtScaledTransferVelocity(schmidt_number = OxygenPolynomialSchmidtNumber(FT)),
                                   water_concentration = OxygenConcentration(),
                                   air_concentration = 9352.7, # mmolO₂/m³
                                   wind_speed = 2,
                                   kwagrs...)
```

水中に溶けた酸素と、`transfer_velocity`を持つ`air_concentration`との間のガス交換のための`FluxBoundaryCondition`を返します（詳細は`GasExchangeBoundaryCondition`を参照してください）。

`kwargs`は`GasExchangeBoundaryCondition`に渡されます。
