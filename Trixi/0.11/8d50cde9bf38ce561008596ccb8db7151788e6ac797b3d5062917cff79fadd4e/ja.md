```
PassiveTracerEquations(flow_equations; n_tracers)
```

`flow_equations` にパッシブトレーサーを追加します。トレーサーは流れの速度によって輸送されます。これは、任意の次元で任意の数のトレーサー `n_tracers` に対して、保存則と非保存則の方程式の両方に対応します。1次元の場合、1つのトレーサー $\chi$ と密度および速度がそれぞれ $\rho, v$ の流れに対して、パッシブトレーサーの方程式は次のようになります。

$$
\frac{\partial \rho \chi}{\partial t} + \frac{\partial}{\partial x} \left( \rho v \chi \right) = 0
$$
