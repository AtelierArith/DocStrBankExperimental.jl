```
TemperatureRatio(pr::PressureRatio,Isentropic[;gas=Air])
```

与えられた圧力比 `pr` に基づいて、2つの点間の温度比を計算します。これは、以下の等エントロピー関係を使用します。

$$
\dfrac{T_2}{T_1} = \left(\dfrac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}
$$
