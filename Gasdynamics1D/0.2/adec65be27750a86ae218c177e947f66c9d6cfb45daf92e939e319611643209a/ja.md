```
T0OverT0Star(M::MachNumber,RayleighFlow[;gas=Air]) -> TemperatureRatio
```

与えられたマッハ数に対して、レイリー流のための停滞温度と音速停滞温度の比を計算します。使用する方程式は次のとおりです。

$$
\dfrac{T_0}{T_0^*} = \dfrac{(\gamma+1)M^2 (2 + (\gamma-1)M^2)}{(1+\gamma M^2)^2}
$$
