```
exsolve(composition::Mafic, P::Float64, T::Float64, X_co2::Float64)::NamedTuple{(:meq, :dmeqdP, :dmeqdT, :dmeqdXco2, :C_co2, :dC_co2dP, :dC_co2dT, :dC_co2dXco2), NTuple{8, Float64}}
```

このスクリプトはLiu et al. (2006)を使用して水の溶解度を計算します。

## 引数

  * `composition`: `Mafic()`
  * `P`: 圧力 (Pa)
  * `T`: 温度 (K)
  * `X_co2`: ガス中のCO2のモル分率。
