```
GasExchange
```

`GasExchange`は、`water_concentration`と`air_concentration`の間の気水フラックスを返し、温度（後で提供される）と`wind_speed`から計算された`transfer_velocity`を使用します。

`transfer_velocity`は風速と温度の関数として振る舞うべきです（すなわち、`k(u, T)`）、`water_concentration`は`c(x, y, t, T, field_dependencies...)`の関数です。

`water_concentration`、`air_concentration`、および`wind_speed`は、数値、形式が`(x, y, t)`の関数、`discrete_form`がtrueに設定されている場合の形式が`(i, j, grid, clock, model_fields)`の関数、または任意の種類の`Field`である可能性があります。

`water_concentration`は通常、トレーサーの名前を持つ`[Tracer]Concentration`であるべきです（これが`OxygenConcentration`でない場合は、自分で構築する必要があります）、または水中のCO₂の部分圧を診断する`CarbonDioxideConcentration`です。
