```
eos_g(P::Float64, T::Float64)::EosG{Float64}
```

ハイパー・クワンのパラメータ化は、Huber et al. 2010から取られています。

## 引数

  * `P`: 圧力 (Pa)
  * `T`: 温度 (K)

## 戻り値

次のフィールドを含む `EosG` 構造体のインスタンス:

  * `rho_g`: ガスの密度 (kg/m³)。
  * `drho_g_dP`: 圧力に関する密度の偏微分 (kg/m³/Pa)。
  * `drho_g_dT`: 温度に関する密度の偏微分 (kg/m³/K)。
