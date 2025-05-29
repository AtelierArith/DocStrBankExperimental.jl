```
VLLE_temperature(model::EoSModel, p; T0 = x0_LLE_temperature(model,p))
```

は、与えられた温度での二成分混合物の蒸気-液体-液体平衡温度と特性を計算します。

タプルを返し、以下を含みます：

  * VLLE温度 `[K]`
  * VLLE点での組成 `x₁` の液体体積 [`m³`]
  * VLLE点での組成 `x₂` の液体体積 [`m³`]
  * VLLE点での組成 `y` の蒸気体積 [`m³`]
  * 液体組成 `x₁`
  * 液体組成 `x₂`
  * 液体組成 `y`
