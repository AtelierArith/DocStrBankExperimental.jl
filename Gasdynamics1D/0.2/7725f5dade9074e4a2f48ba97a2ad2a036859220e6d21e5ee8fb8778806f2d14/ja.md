```
PressureRatio(dr::DensityRatio,Isentropic[;gas=Air])
```

等エントロピー的に接続された2点間の圧力比を計算します。これには、これら2点間の密度比 `dr` を使用し、等エントロピー関係を用います。

$$
\dfrac{p_2}{p_1} = \left(\dfrac{\rho_2}{\rho_1}\right)^{\gamma}
$$
