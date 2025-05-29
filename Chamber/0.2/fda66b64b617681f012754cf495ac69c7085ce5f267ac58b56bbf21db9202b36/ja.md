```
exsolve3(composition::Silicic, P::Float64, T::Float64, m_eq::Float64)::NamedTuple{(:C_co2, :X_co2), NTuple{2, Float64}}
```

圧力、温度、および水の量を使用して、ニュートン・ラフソン法を用いてCO2の濃度とX_CO2を解決します。

## 引数

  * `composition`: `Silicic()`
  * `P`: 圧力 (Pa)
  * `T`: 温度 (K)
  * `m_eq`: 水の量

## 戻り値

次のフィールドを持つNamedTuple:

  * `C_co2`: 溶融物中のCO2の濃度。
  * `X_co2`: ガス中のCO2のモル分率。
