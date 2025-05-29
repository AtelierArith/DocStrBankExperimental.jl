```
TemperatureRatio(dr::DensityRatio,Isentropic[;gas=Air])
```

与えられた密度比 `dr` を使用して、2つの点間の温度比を計算します。これは、エントロピーが一定の関係を用いています。

$$
\dfrac{T_2}{T_1} = \left(\dfrac{\rho_2}{\rho_1}\right)^{\gamma-1}
$$
