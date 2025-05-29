```
LLE_temperature(model::EoSModel, p, x; T0 = x0_LLE_temperature(model,p,x))
```

は、与えられた圧力での液-液平衡温度と特性を計算します。

次の要素を含むタプルを返します：

  * LLE圧力 `[Pa]`
  * LLE点での組成 `x₁ = x` の液体体積 [`m³`]
  * LLE点での組成 `x₂` の液体体積 [`m³`]
  * 液体組成 `x₂`
