```
GasExchangeBoundaryCondition(; water_concentration,
                               air_concentration,
                               transfer_velocity,
                               wind_speed)
```

`water_concentration`と`air_concentration`の間のガス交換のための`FluxBoundaryCondition`を`transfer_velocity`で返します。

`water_concentration`、`air_concentration`、および`wind_speed`は、数値、形式が`(x, y, t)`の関数、`discrete_form`がtrueに設定されている場合の形式が`(i, j, grid, clock, model_fields)`の関数、または任意の種類の`Field`である可能性があります。

`water_concentration`は通常、トレーサーの名前が含まれる`[Tracer]Concentration`である必要があります（これが`OxygenConcentration`でない場合は、自分で構築する必要があります）、または水中のCO₂の部分圧を診断する`CarbonDioxideConcentration`です。

`transfer_velocity`は形式が`k(u₁₀, T)`の関数である必要があります。
