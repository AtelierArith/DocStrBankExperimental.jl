```
TOverTStar(M::MachNumber,RayleighFlow[;gas=Air]) -> TemperatureRatio
```

与えられたマッハ数に対して、レイリー流のための音速温度に対する温度の比を計算します。この式を使用します。

$$
\dfrac{T}{T^*} = \dfrac{(\gamma+1)^2 M^2}{(1+\gamma M^2)^2}
$$
