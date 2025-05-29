```
BerendsenThermostat(temperature, coupling_const)
```

温度を制御するためのベルンデンサーモスタット。

各ステップの速度のスケーリング因子は

$$
\lambda^2 = 1 + \frac{\delta t}{\tau} \left( \frac{T_0}{T} - 1 \right)
$$

このサーモスタットは、シミュレーションアーティファクトを引き起こす可能性があるため、注意して使用する必要があります。
