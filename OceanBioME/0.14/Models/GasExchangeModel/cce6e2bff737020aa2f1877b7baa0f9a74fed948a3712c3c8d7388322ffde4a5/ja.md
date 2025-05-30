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

`FluxBoundaryCondition`を返します。これは、`carbon_chemisty`モデルによって指定された水中に溶けた二酸化炭素と、`transfer_velocity`を持つ`air_concentration`との間のガス交換を表します（詳細は`GasExchangeBoundaryCondition`を参照してください）。

`silicate_and_phosphate_names`は、`nothing`、シンボルの`Tuple`（珪酸塩およびリン酸塩トレーサーの名前を指定）、または`carbon_chemistry`モデルの値の`NamedTuple`のいずれかである必要があります。

`kwargs`は`GasExchangeBoundaryCondition`に渡されます。

注意: モデルは常に`T`、`S`、`DIC`、および`Alk`がモデルに存在することを要求します。
