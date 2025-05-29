```
exsolve_meq(composition::Silicic, P::Float64, T::Float64, X_co2::Float64)::Float64
```

`meq`のみを計算する`exsolve`の特化版です。

## 引数

  * `composition`: `Silicic()`
  * `P`: 圧力 (Pa)
  * `T`: 温度 (K)
  * `X_co2`: ガス中のCO2のモル分率。

## 戻り値

  * `meq`: 水の量
